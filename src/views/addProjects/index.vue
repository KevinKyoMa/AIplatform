<template>
    <div class="app-container">
        <el-form ref="form" :model="form" label-width="80px">
            <el-form-item label="项目名称">
                <el-input v-model="form.title"></el-input>
            </el-form-item>
            <el-form-item label="项目时间">
                <el-col :span="5">
                    <el-date-picker type="date" placeholder="选择日期" v-model="form.dateRange.start" style="width: 100%;"></el-date-picker>
                </el-col>
                <el-col  :span="1" style="text-align:center" >至</el-col>
                <el-col :span="5">
                    <el-date-picker type="date" placeholder="选择日期" v-model="form.dateRange.end" style="width: 100%;"></el-date-picker>
                </el-col>
            </el-form-item>
            <el-row :gutter="20">
                <el-col :span="12">
                    <el-form-item label="项目环境">
                        <el-select v-model="form.environment" multiple placeholder="请选择项目环境" style="width:100%">
                            <el-option label="Tensorflow 1.8" value="Tensorflow 1.8"></el-option>
                            <el-option label="Python 3.6" value="Python 3.6"></el-option>
                        </el-select>
                    </el-form-item>
                </el-col>
                <el-col :span="12">
                    <el-form-item label="项目成员">
                        <el-select v-model="form.members" multiple placeholder="请选择项目成员" style="width:100%">
                            <el-option label="张凤荔" value="张凤荔"></el-option>
                            <el-option label="王瑞锦" value="王瑞锦"></el-option>
                            <el-option label="张志扬" value="张志扬"></el-option>
                            <el-option label="汤启友" value="汤启友"></el-option>
                            <el-option label="xxx" value="xxx"></el-option>
                        </el-select>
                    </el-form-item>
                </el-col>
            </el-row>
            
            
            <el-form-item label="项目简介">
                <el-input type="textarea" v-model="form.info"></el-input>
            </el-form-item>
            <el-form-item label="项目正文">
                <div class="markdown">
                    <mavon-editor
                        ref="md"
                        v-model="mavonValue"
                        @imgAdd="uploadImg"
                        @change="change"
                        :codeStyle="configs.codeStyle"/>
                </div>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="onSubmit">添加项目</el-button>
                <el-button>取消</el-button>
            </el-form-item>

        </el-form>
    </div>
</template>

<script>
  export default {
      
    data() {
      return {
        form: {
          title: '',
          dateRange: {
              start:'',
              end:''
          },
          environment: [],
          members:[],
          info: '',
          detail: '',
        },
        mavonValue: '',//markdown内容
        mavonHtml: '',//markdown的Html内容
        configs:{ //markdown的设置
            codeStyle: 'vs2015', // 代码风格配色，
        },
      }
    },
    methods: {
      onSubmit() {
          
          console.log(this.mavonValue)
          console.log(this.mavonHtml)
          console.log('submit!');
      },
    uploadImg(pos, file) {
        var formData = new FormData();
        formData.append('image', file);
        this.$axios({
            url: '文件服务器地址',
            method: "post",
            data: formData,
            headers: {
                'Content-Type': 'multipart/form-data'
            }
        }).then((url) => {
            //使用服务器返回的图片地址替换原图片地址
            $vm.$img2Url(pos, url);
        })
    },
      //所有的操作都被解析重新渲染
      change(value, render){
          //render为 markdown解析后的结果[html]
          this.html = render
      },

    }
  }
</script>