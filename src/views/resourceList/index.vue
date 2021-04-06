<template>
    <div class="app-container">
        <el-card class="box-card">
            <el-table
                ref="filterTable"
                :data="tableData"
                style="width: 100%"
                max-height="800">
                <el-table-column
                fixed
                prop="date"
                label="日期"
                sortable
                width="180"
                column-key="date"
                :filters="[{text: '2016-05-01', value: '2016-05-01'}, {text: '2016-05-02', value: '2016-05-02'}, {text: '2016-05-03', value: '2016-05-03'}, {text: '2016-05-04', value: '2016-05-04'}]"
                :filter-method="filterHandler"
                >
                </el-table-column>
                <el-table-column
                prop="title"
                label="论文名称"
                width="300"
                >
                </el-table-column>
                <el-table-column
                prop="members"
                label="作者"
                >
                </el-table-column>
                <el-table-column
                prop="target"
                label="投往期刊（会议）"
                >
                </el-table-column>
                <el-table-column
                prop="statu"
                label="状态"
                width="100"
                
                >
                    <template slot-scope="scope">
                        <el-tag
                        :type="scope.row.statu === '已通过' ? 'success' : 'warning'"
                        disable-transitions>{{scope.row.statu}}</el-tag>
                    </template>
                </el-table-column>
                <el-table-column
                prop="keywords"
                label="关键词"
                width="200"
                :filters="[{ text: 'CNN', value: 'CNN' }, { text: '知识图谱', value: 'knowledgeGraph' }]"
                >
                <template slot-scope="scope">
                    <el-tag
                        disable-transitions>{{scope.row.keywords}}
                    </el-tag>
                </template>
                </el-table-column>

                <el-table-column
                    fixed="right"
                    label="操作"
                    width="120">
                    <template slot-scope="scope">
                        <el-button @click="handleClick(scope.row.url)" type="text" size="small">查看</el-button>
                        <el-button
                        @click.native.prevent="deleteRow(scope.$index, tableData)"
                        type="text"
                        size="small">
                        移除
                        </el-button>
                    </template>
                </el-table-column>
            </el-table>
        </el-card>
    </div>
    
</template>

<script>
export default {
    data(){
        return{
            tableData: [{
                date: '2021-4-01',
                title: '基于分层注意力的信息级联预测模型',
                members: '张志扬',
                keywords: 'CNN',
                target:'xxxx报',
                statu:'已通过',
                abstract:'',
                url:'http://image.cache.timepack.cn/nodejs.pdf'
                }, {
                date: '2021-4-01',
                title: '基于改进Eclat算法的资源池节点异常模式挖掘',
                members: '高强',
                keywords: 'test',
                target:'xxxx会议',
                statu:'已通过',
                abstract:'',
                url:''
                }, {
                date: '2021-4-01',
                title: 'Predicting Human Mobility via Variational Attention',
                members: 'xxx',
                keywords: '知识图谱',
                target:'xxxxx报',
                statu:'已通过',
                abstract:'',
                url:''
                },]
        }
    },
    methods: {
        deleteRow(index, rows) {
            rows.splice(index, 1);
        },
        formatter(row, column) {
            return row.address;
        },
        filterTag(value, row) {
            
            return row.statu === value;
        },
        filterHandler(value, row, column) {
            const property = column['property'];
            return row[property] === value;
        },
        handleClick(pdfUrl) {
            window.open(pdfUrl, "_blank")
        }
    }
}
</script>