<template>
    <div class="app-container">
        <el-row :gutter="20">
            <el-col :span="18">
                <el-card class="box-card" v-if="Pj_Detail">
                    <div slot="header" class="clearfix">
                        <span>{{Pj_Detail.title}}</span>
                        <el-button style="float: right; padding: 3px 0" type="text">修改</el-button>
                    </div>
                    <div class="intro">
                        <div class="dateRange">
                            <span>项目时间： </span>
                            <span>{{Pj_Detail.dateRange.start}}</span>
                            <span>至</span>
                            <span>{{Pj_Detail.dateRange.end}}</span>
                        </div>
                        <div class="env_mem" style="padding:10px 0px 30px 0px">
                            <span class="left" style="width:50%;display:block;float:left">
                                <span>项目环境： </span>
                                <span>{{Pj_Detail.environment}}</span>
                            </span>
                            <span class="right" style="width:50%;display:block;float:left">
                                <span>项目成员： </span>
                                <span>{{Pj_Detail.member}}</span>
                            </span>
                        </div>
                        <div class="intro" style="padding:0px 0px 30px 0px">
                            <span>项目简介： </span>
                            <span>{{Pj_Detail.info}}</span>
                        </div>
                    </div>
                    <div class="detail">
                        {{Pj_Detail.info}}
                    </div>
                </el-card>
            </el-col>
            <el-col :span="6">
                <el-card class="box-card" v-if="Pj_Detail">
                    <div slot="header" class="clearfix">
                        <span>资源下载</span>
                        <el-button style="float: right; padding: 3px 0" type="text">批量下载</el-button>
                    </div>
                    <div class="resourceBox">
                        <div class="title" style="padding:12px 0">论文列表</div>
                        <div class="container" style="background-color:#dfdfdf4d;padding:10px">
                            <div v-for="o in 5" :key="o">
                                <a style="color:#71b8f5;display:block;margin-bottom:5px" >论文11111</a>
                            </div>
                        </div>

                        <div class="title" style="padding:12px 0">数据集</div>
                        <div class="container" style="background-color:#dfdfdf4d;padding:10px">
                            <div v-for="o in 4" :key="o">
                                <a style="color:#71b8f5;display:block;margin-bottom:5px" >数据集 {{o}}</a>
                            </div>
                        </div>

                        <div class="title" style="padding:12px 0">算法模型</div>
                        <div class="container" style="background-color:#dfdfdf4d;padding:10px">
                            <div v-for="o in 2" :key="o">
                                <a style="color:#71b8f5;display:block;margin-bottom:5px" >模型 {{o}}</a>
                            </div>
                        </div>

                        <div class="title" style="padding:12px 0">代码包</div>
                        <div class="container" style="background-color:#dfdfdf4d;padding:10px">
                            <div v-for="o in 1" :key="o">
                                <a style="color:#71b8f5;display:block;margin-bottom:5px" >代码包 {{o}}</a>
                            </div>
                        </div>
                    </div>
                </el-card>
            </el-col>
        </el-row>
        
    </div>
</template>

<script>
export default {
    data(){
        return{
            Projects:[
                {
                title: '人工智能项目111111',
                dateRange:{
                    start: '2020-01-01',
                    end: '2022-01-01'
                },
                info: '该项目立项于2020年1月1日xxxx该段是测试文字该段是测试文字该段是测试文字该段是测试文字该段是测试文字',
                environment: 'Tensorflow 1.8',
                member: '张凤荔、王瑞锦、XXX、XXX、XXX',
                dataset:[],
                detail:[],
                }, 
                {
                title: '人工智能项目22222',
                dateRange:{
                    start: '2020-01-01',
                    end: '2022-01-01'
                },
                info: '该项目立项于2020年1月1日xxxx该段是测试文字该段是测试文字该段是测试文字该段是测试文字该段是测试文字',
                environment: 'Tensorflow 1.8',
                dataset:[],
                detail:[],
                }, 
            ],

            Pj_Detail:[

            ],
        }
    },
    mounted(){
        console.log(this.$route.params)
        this.Pj_Detail = this.$route.params.data
    }
}
</script>

<style>
  .text {
    font-size: 14px;
  }

  .item {
    margin-bottom: 18px;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }
  .clearfix:after {
    clear: both
  }

  
</style>