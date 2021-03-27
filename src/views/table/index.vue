<template>
  <div class="app-container">
    <el-card style="margin-bottom:20px;padding-bottom:20px;height:10.625rem" class="box-card projectList"  v-for="project in Projects" :key="project" >
      <a >
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
              <span v-for="mber in project.member" :key="mber">{{mber}}  </span>
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
      Projects:[
        {
          title:'人工智能项目111111',
          dateRange:{
            start:'2020-01-01',
            end:'2022-01-01'
          },
          info:'该项目立项于2020年1月1日xxxx该段是测试文字该段是测试文字该段是测试文字该段是测试文字该段是测试文字',
          environment:'Tensorflow 1.8',
          member:[
            '张凤荔',
            '王瑞锦',
            'XXX'
          ],
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
      ]
    }
  },
  created() {
    
  },
  methods: {
   
  }
}
</script>

<style lang="stylus">

</style>
