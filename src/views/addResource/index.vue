<template>
    <div class="app-container">
        <el-card class="box-card">
            <el-upload
                class="upload-demo"
                drag
                action="https://jsonplaceholder.typicode.com/posts/"
                multiple>
                <i class="el-icon-upload"></i>
                <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
                
            </el-upload>
            <el-form ref="form" :model="form" label-width="80px">
                <el-form-item label="资源名称">
                    <el-input v-model="form.title"></el-input>
                </el-form-item>
                <el-form-item label="资源时间">
                    <el-col :span="5">
                        <el-date-picker type="date" placeholder="选择日期" v-model="form.dateRange.start" style="width: 100%;"></el-date-picker>
                    </el-col>  
                </el-form-item>
                <el-row :gutter="20">
                    <el-col :span="12">
                        <el-form-item label="资源类型">
                            <el-select v-model="form.environment" multiple placeholder="请选择资源类型" style="width:100%">
                                <el-option label="数据集" value="DataSet"></el-option>
                                <el-option label="论文" value="Ariticle"></el-option>
                                <el-option label="算法模型" value="algoModel"></el-option>
                                <el-option label="算法包" value="algoPack"></el-option>
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
                
                
                <el-form-item label="资源简介">
                    <el-input type="textarea" v-model="form.info"></el-input>
                </el-form-item>
                
                <el-form-item>
                    <el-button type="primary" @click="onSubmit">添加资源</el-button>
                    <el-button>取消</el-button>
                </el-form-item>

            </el-form>
        </el-card>
        
    </div>
</template>

<script>
export default {
    data(){
        return{
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
        }
    }
}
</script>