<template>
  <div class="app-container">
    <el-button type="text" @click="dialogVisible = true" @click.native="drawCharts();">点击打开数据可视化面板demo</el-button>
    <el-dialog
      :title="dataChartsTitle"
      :visible.sync="dialogVisible"
      width="60%"
      :before-close="handleClose"
    >
      <el-tabs v-model="activeName" @tab-click="handleClick">
        <el-tab-pane label="数据表格" name="excels">
          <el-table
            v-loading="listLoading"
            :data="list"
            element-loading-text="Loading"
            height="450"
            border
            fit
            highlight-current-row
          >
            <el-table-column align="center" label="ID" width="95">
              <template slot-scope="scope">{{ scope.$index }}</template>
            </el-table-column>
            <el-table-column label="Title">
              <template slot-scope="scope">{{ scope.row.title }}</template>
            </el-table-column>
            <el-table-column label="Author" width="110" align="center">
              <template slot-scope="scope">
                <span>{{ scope.row.author }}</span>
              </template>
            </el-table-column>
            <el-table-column label="Pageviews" width="110" align="center">
              <template slot-scope="scope">{{ scope.row.pageviews }}</template>
            </el-table-column>
            <el-table-column class-name="status-col" label="Status" width="110" align="center">
              <template slot-scope="scope">
                <el-tag :type="scope.row.status | statusFilter">{{ scope.row.status }}</el-tag>
              </template>
            </el-table-column>
            <el-table-column align="center" prop="created_at" label="Display_time" width="200">
              <template slot-scope="scope">
                <i class="el-icon-time" />
                <span>{{ scope.row.display_time }}</span>
              </template>
            </el-table-column>
          </el-table>
        </el-tab-pane>
        <el-tab-pane label="柱状图"  name="ColumnChart">
          <div id="ColumnChart" ref="chart" style="width: 600px;height:400px;"></div>
        </el-tab-pane>
        <el-tab-pane label="饼图" name="PieChart">
          <div id="PieChart" ref="chart" style="width: 600px;height:400px;"></div>
        </el-tab-pane>
        <el-tab-pane label="折线图" name="LineChart">
          <div id="LineChart" ref="chart" style="width: 600px;height:400px;"></div>
        </el-tab-pane>
      </el-tabs>
    </el-dialog>
  </div>
</template>
<script>
import { getList } from "@/api/table";
import { Breadcrumb } from 'element-ui';

export default {
  filters: {
    statusFilter(status) {
      const statusMap = {
        published: "success",
        draft: "gray",
        deleted: "danger",
      };
      return statusMap[status];
    },
  },
  data() {
    return {
      dialogVisible: false,
      list: null,
      listLoading: true,
      dataChartsTitle: "数据预处理可视化",

      //可视化面板tab active数
      activeName: "first",
      //用于储存图表及数据
      charts:[
        {
          label:'柱状图',
          id:"ColumnCharts",
          data:[
            ['First',1,2,3],
            ['second',4,1,5],
            ['third',2,3,4],
            ['forth',6,2,1],
          ]
        },
        {
          label:'饼图',
          id:"pieCharts",
          data:[
            ['First',14,2,3],
            ['second',4,5,5],
            ['third',21,13,4],
            ['forth',6,22,1],
          ]
        },
        {
          label:'折线图',
          id:"LineCharts",
          data:[
            ['First',10,11,5],
            ['second',24,4,6],
            ['third',2,15,5],
            ['forth',5,13,1],
          ]
        },
        
      ]
    };
  },
  created() {
    this.fetchData();
  },
  mounted() {
    
  },
  methods: {
    handleClose(done) {
      this.$confirm("确认关闭？")
        .then((_) => {
          done();
        })
        .catch((_) => {});
    },
    handleClick(tab, event) {
      console.log(tab, event);

      //这部分是将画图函数与tab组件融合起来，通过tab的点击事件来调用画图函数，将图表信息传入函数
      if(tab.name !== 'excels'){
        var chartType = ''
        var dataIndex = 0
        switch (tab.name) {
          case 'ColumnChart':
            chartType = 'bar'
            dataIndex = 0
            break;
          case 'PieChart':
            chartType = 'pie'
            dataIndex = 1
            break;
          case 'LineChart':
            chartType = 'line'
            dataIndex = 2
            break;
          default:
            break;
        }
        this.drawCharts(tab.name,chartType,dataIndex)
      }
    },
    fetchData() {
      this.listLoading = true;
      getList().then((response) => {
        this.list = response.data.items;
        this.listLoading = false;
      });
    },
    drawCharts(chartID,chartType,dataIndex) {
      //chartID指图表元素的id 用以捕获元素；chartType为图表类型；dataIndex用以选择图表的数据索引
      let that = this
      console.log("start!")
      // 基于准备好的dom，初始化echarts实例
      let Chart = document.getElementById(chartID);
      console.log(Chart)
      let myChart = this.$echarts.init(Chart);
      // 指定图表的配置项和数据
      let option = {
        title: {
          text: "数据可视化测试",
        },
        tooltip: {},
        legend: {
          data: ["销量"],
        },
        xAxis: {
          type:'category'
        },
        yAxis: {},
        dataset:{
          source:that.charts[dataIndex].data,
        },
        series:chartType=='pie'?
        //通过表达式来判断特殊的图表
         [
          {
            name:'测试1',
            type: chartType,
            encode:{itemName:0,value:1}
          }
        ]
        :
        [
          {
            name:'测试1',
            type: chartType,
            encode:{x:0,y:1}
          },
          {
            name:'测试2',
            type: chartType,
            encode:{x:0,y:2},
          },
          {
            name:'测试3',
            type: chartType,
            encode:{x:0,y:3},
          },

        ]
      };
      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    },
  },
};
</script>