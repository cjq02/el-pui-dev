<template>
  <div class="table-container">
    <div style="margin-top: 10px;height:100%;width:55%;padding-right:10px;">
      <el-card class="card-box" :body-style="{ padding: '0px' }">
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
                  prop="entpName"
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
                  prop="salePhase"
                  label="售前阶段"
                  header-align="center"
                />
                <el-table-column
                  prop="lastContactsTime"
                  label="最近联系"
                  header-align="center"
                />
                <el-table-column
                  prop="monthTimes"
                  label="30天联系"
                  header-align="center"
                />
                <el-table-column
                  prop="prodLineCode"
                  label="产品线"
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
      </el-card></div>
    <div style="height:100%;margin-top:10px;width:45%">
      <div style="height:50%;padding: 0 0 5px 0;">
        <el-card class="card-box" :body-style="{ padding: '0px' }">
          <div class="header">
            <div class="wrapper">
              <crm-title-tabs v-model="myBacklogTabIndex" :data="myBacklogTabsData" />
            </div>
          </div>
          <div class="content">
            <el-row>
              <el-col :span="24" style="padding:20px;">
                <el-table
                  height="200px"
                  :data="tableData"
                  style="width: 100%;"
                  border
                >
                  <el-table-column
                    prop="corpName"
                    label="日期"
                    header-align="center"
                  />
                  <el-table-column
                    prop="area"
                    label="类型"
                    header-align="center"
                  />
                  <el-table-column
                    prop="level"
                    label="阶段"
                    header-align="center"
                  />
                  <el-table-column
                    prop="preSaleStage"
                    label="联系人"
                    header-align="center"
                  />
                  <el-table-column
                    prop="recentContactCount"
                    label="内容"
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
      </div>
      <div style="height:50%;padding: 5px 0 0 0;">
        <el-card class="card-box" :body-style="{ padding: '0px' }">
          <div class="header">
            <div class="wrapper">
              <crm-title-tabs v-model="myWorkTabIndex" :data="myWorkTabsData" />
            </div>
          </div>
          <div class="content">
            <el-row>
              <el-col :span="24" style="padding:20px;">
                <el-table
                  height="200px"
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
      </div>
    </div>
  </div>
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
      myBacklogTabsData: ['我的待办', '消息通知'],
      myBacklogTabIndex: 0,
      myWorkTabsData: ['我的工作', '我的产品'],
      myWorkTabIndex: 0,
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
.table-container {
  display: flex;flex-direction: row;justify-content: space-between;height:700px;

  .card-box {
    border-radius: 10px;
    font-size: 14px;
    height: 100%;
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
}
</style>
