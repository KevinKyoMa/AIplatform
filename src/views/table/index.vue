<template>
  <div class="app-container">
    <el-card style="margin-bottom:20px;padding-bottom:20px;height:10.625rem" class="box-card projectList"  v-for="(project,index) in Projects" :key="project" >
      <a  @click="showDetail(index)" >
        <div class="left" style="float:left;width:48.5%">
          <div class="title">
            <p>{{project.title}}</p>
          </div>
          <div class="Info">
            <span class="date" style="display:block;padding-bottom:8px">
              <i>{{project.dateRange.start}} </i>
              <i>至 </i>
              <i>{{project.dateRange.end}} </i>
            </span>
            <span class="pro-2" style="display:block;padding-bottom:8px">
              <span>项目环境：</span>
              <span>{{project.environment}}</span>
            </span>
            <span class="pro-2" style="display:block;padding-bottom:8px">
              <span>团队情况: </span>
              <span>{{mber}}</span>
            </span>
          </div>
        </div>
        <el-divider direction="vertical" style="height：8rem;float:left"></el-divider>
        <div class="right" style="float:left;width:48.5%;background: #80808021;padding:15px 8px 15px 8px">
          <div class="Info-2">
            <p style="margin:0;height:6rem">{{project.info}}</p>
          </div>
        </div>
        
      </a>
    </el-card>
    <el-pagination
      background
      layout="prev, pager, next"
      :total="1">
    </el-pagination>
    <!--项目详情-->
    <el-dialog
      :title="Pj_Detail.title"
      :visible.sync="centerDialogVisible"
      width="60%"
      height="37rem"
      center>
      <el-divider content-position="left"  v-if="Pj_Detail.dateRange">{{Pj_Detail.dateRange.start}} 至 {{Pj_Detail.dateRange.end}}</el-divider>
      <div class="intro">
        <p>团队情况： {{Pj_Detail.member}}</p>
        <p>项目环境： {{Pj_Detail.environment}}</p>
      </div>
      <span>{{Pj_Detail.info}}</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="centerDialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="centerDialogVisible = false">确 定</el-button>
      </span>
    </el-dialog>
   
  </div>
</template>

<script>



export default {
  filters: {
    
  },
  data() {
    return {
      list: null,
      listLoading: true,

      centerDialogVisible: false, //控制详情显式
      Projects:[
        {
          title:'人工智能项目111111',
          dateRange:{
            start:'2020-01-01',
            end:'2022-01-01'
          },
          info:'该项目立项于2020年1月1日xxxx该段是测试文字该段是测试文字该段是测试文字该段是测试文字该段是测试文字',
          environment:'Tensorflow 1.8',
          member:'张凤荔、王瑞锦、XXX、XXX、XXX',
          dataset:[],
          detail:[],
        }, 
        {
          title:'人工智能项目22222',
          dateRange:{
            start:'2020-01-01',
            end:'2022-01-01'
          },
          info:'该项目立项于2020年1月1日xxxx该段是测试文字该段是测试文字该段是测试文字该段是测试文字该段是测试文字',
          environment:'Tensorflow 1.8',
          dataset:[],
          detail:[],
        }, 
      ],

      Pj_Detail:[

      ],
    }
  },
  created() {
    
  },
  methods: {
    showDetail(index){
      //用来展示详情
      this.centerDialogVisible = true

      this.Pj_Detail = this.Projects[index]

      console.log(this.Pj_Detail)
    }
  }
}
</script>

<style lang="stylus">

</style>
