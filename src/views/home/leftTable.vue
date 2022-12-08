<template>
  <el-card class="card-box" style="margin-top: 10px;" :body-style="{ padding: '0px' }">
    <div class="header">
      <div class="wrapper">
        <crm-title-tabs :value="myCustomTabIndex" :data="myCustomTabsData" />
        <div class="search-item">
          <div class="item-label">名称：</div>
          <div class="item-input">
            <el-select v-model="searchModel.name" size="mini" class="type1" placeholder="请选择">
              <el-option
                v-for="item in options"
                :key="item.value"
                :label="item.label"
                :value="item.value"
              />
            </el-select>
          </div>
        </div>
        <div class="search-item">
          <div class="item-label">阶段：</div>
          <div class="item-input">
            <el-select v-model="searchModel.stage" class="type1" placeholder="请选择" size="mini">
              <el-option
                v-for="item in options"
                :key="item.value"
                :label="item.label"
                :value="item.value"
              />
            </el-select>
          </div>
        </div>
        <div class="search-item">
          <el-button class="button" type="primary" size="mini" @click="search">查询</el-button>
        </div>
      </div>
    </div>
    <div class="content">
      <el-row class="table-summary">
        <el-col :span="4">意向：14</el-col>
        <el-col :span="4">待签：14</el-col>
        <el-col :span="4">普通：14</el-col>
        <el-col :span="4">新客户：14</el-col>
      </el-row>
      <el-row>
        <el-col :span="24" style="padding:20px;">
          <el-table
            height="500px"
            :data="tableData"
            style="width: 100%;"
            border
          >
            <el-table-column
              prop="corpName"
              label="企业名称"
              header-align="center"
            />
            <el-table-column
              prop="area"
              label="地区"
              header-align="center"
            />
            <el-table-column
              prop="level"
              label="等级"
              header-align="center"
            />
            <el-table-column
              prop="preSaleStage"
              label="售前阶段"
              header-align="center"
            />
            <el-table-column
              prop="recentContactCount"
              label="最近联系"
              header-align="center"
            />
            <el-table-column
              prop="monthContactCount"
              label="30天联系"
              header-align="center"
            />
            <el-table-column
              prop="productLine"
              label="30天联系"
              header-align="center"
            />
            <el-table-column
              prop="_operate"
              label="操作"
              header-align="center"
            />
          </el-table>
        </el-col>
      </el-row>
    </div>
  </el-card>
</template>
<script>
import CrmTitleTabs from '@/components/crmTitleTabs'

export default {
  components: {
    CrmTitleTabs
  },
  data() {
    return {
      myCustomTabsData: ['我的客户'],
      myCustomTabIndex: 1,
      tableData: [],
      searchModel: {
        name: '',
        stage: ''
      },
      options: [{
        value: '选项1',
        label: '黄金糕'
      }, {
        value: '选项2',
        label: '双皮奶'
      }, {
        value: '选项3',
        label: '蚵仔煎'
      }, {
        value: '选项4',
        label: '龙须面'
      }, {
        value: '选项5',
        label: '北京烤鸭'
      }]
    }
  },
  methods: {
    search() {}
  }
}
</script>
<style scoped lang="scss">
.card-box {
  border-radius: 10px;
  font-size: 14px;
  .header {
    height: 60px;
    background: #F0F2F5;
    opacity: 0.6;

    .wrapper {
      padding: 12px 24px 0 24px;
      display: flex;
      flex-direction: row;
    }
  }

  .content {
    height: 265px;
  }
}

.search-item {
  display: flex;
  padding: 10px;
  flex-direction: row;
  .item-label {
    width: 80px;
    text-align: right;
    line-height: 28px;
  }
  .item-input {

  }
}
.table-summary {
  padding: 20px 0 0 30px;
}
</style>
