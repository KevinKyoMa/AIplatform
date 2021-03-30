<template>
  <div class="dashboard-container">
    <div class="dashboard-text"></div>
    <el-row :gutter="20">
      <el-col :span="17">
        <el-card class="box-card">
          <div class="title">
            <h3>网络与数据安全实验室</h3>
          </div>
          <div class="main-body">
            <p>网络与数据安全实验室一直致力于信息安全领域的学科建设、人才培养、科学研究与技术应用。2008年12月通过四川省科技厅的评审，批准建设网络与数据安全四川省重点实验室。</p>
            <p>实验室主任为秦志光教授，实验室固定研究人员20人，其中博士生导师4人，教授4人，副教授及高级工程师16人，讲师4人，博士和硕士研究生100余人。</p>
            <p>实验室在网络安全与密码学、移动网络应用与安全、物联网应用与安全、云计算应用安全、自然语言处理与数据挖掘等领域取得了系列研究成果。</p>
            <img src="@/assets/dashboardImges/hezhao1.jpg" alt="团队合照">
            <p>
              <span class="title-2">实验室主任：</span>
              <span>秦志光</span>
            </p>
            <p>
              秦志光，博士、教授、博士生导师、国家特殊津贴获得者、国务院学位委员会第六届学科评议组成员、四川省学术和技术带头人、中共党员。中国计算机学会理事，教育部高等学校信息安全类教学指导委员会委员，教育部高等学校实验室建设指导委员会委员，国家自然科学基金同行评议专家，国家科技部、教育部同行评议专家，国家信息安全成果产业化基地（西部）专家组成员，四川省计算机用户协会理事长，四川省软件行业协会常务副理事长，四川省计算机学会副理事长，四川省科技厅电子信息技术专家组成员，四川省保密技术专家咨询小组成员，四川省软件企业认定专家组成员，国家软件评测中心认证专家，四川省咨询业协会教授级咨询师，国际电子电器工程师学会（IEEE）会员，多份核心期刊编委。
            </p>
            <p>
              <span class="title-2">实验室主要成员：</span>
              <span>...</span>
            </p>
          </div>
        </el-card>
      </el-col>
      <el-col :span="7">
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>项目情况</span>
            <el-button style="float: right; padding: 3px 0" type="text">
              <a href="#/projects/pInfo">查看</a>
            </el-button>
          </div>
          <div class="project-info">
            <div>
              <span class="title">实验室项目：</span>
              <span class="number-total">2</span>
              <span>个</span>
            </div>
            <div>
              <span class="title">在研项目：</span>
              <span class="number-processing">2</span>
              <span>个</span>
            </div>
            <div>
              <span class="title">已结题项目：</span>
              <span class="number-done">0</span>
              <span>个</span>
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

    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
