<template>
  <div class="tables-container">
    <div class="table-box" style="width:55%;padding: 10px;">
      <el-row>
        <el-col :span="8">
          <div class="search-item">
            <div class="item-label">名称：</div>
            <div class="item-input">
              <el-select v-model="searchModel.name" size="mini" />
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="search-item">
            <div class="item-label">阶段：</div>
            <div class="item-input">
              <el-select v-model="searchModel.stage" size="mini" />
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="search-item">
            <el-button class="button" type="primary" size="mini" @click="search">查询</el-button>
          </div>
        </el-col>
      </el-row>
      <el-row class="summary">
        <el-col :span="4">意向：14</el-col>
        <el-col :span="4">待签：14</el-col>
        <el-col :span="4">普通：14</el-col>
        <el-col :span="4">新客户：14</el-col>
      </el-row>
      <el-row>
        <el-col :span="24">
          <el-table
            height="500px"
            :data="tableData"
            style="width: 100%"
            border
          >
            <el-table-column
              prop="corpName"
              label="企业名称"
              width="180"
            />
            <el-table-column
              prop="area"
              label="地区"
              width="180"
            />
            <el-table-column
              prop="level"
              label="等级"
              width="180"
            />
            <el-table-column
              prop="preSaleStage"
              label="售前阶段"
            />
            <el-table-column
              prop="recentContactCount"
              label="最近联系"
            />
            <el-table-column
              prop="monthContactCount"
              label="30天联系"
            />
            <el-table-column
              prop="productLine"
              label="30天联系"
            />
            <el-table-column
              prop="_operate"
              label="操作"
            />
          </el-table>
        </el-col>
      </el-row>
    </div>
    <div style="width:45%;padding: 10px;">
      <el-table
        :data="tableData"
        style="width: 100%"
        border
      >
        <el-table-column
          prop="corpName"
          label="企业名称"
          width="180"
        />
        <el-table-column
          prop="area"
          label="地区"
          width="180"
        />
        <el-table-column
          prop="level"
          label="等级"
          width="180"
        />
        <el-table-column
          prop="preSaleStage"
          label="售前阶段"
        />
        <el-table-column
          prop="recentContactCount"
          label="最近联系"
        />
        <el-table-column
          prop="monthContactCount"
          label="30天联系"
        />
        <el-table-column
          prop="productLine"
          label="30天联系"
        />
        <el-table-column
          prop="_operate"
          label="操作"
        />
      </el-table>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tableData: [],
      searchModel: {
        name: '',
        stage: ''
      }
    }
  },
  methods: {
    search() {}
  }
}
</script>
<style scoped lang="scss">
.tables-container {
  background-color: #dde0e5;
  padding: 10px;
  display: flex;
  flex-direction: row;

  .table-box {
    background-color: #ffffff;
    .summary {
      padding: 10px;

    }
  }

  .search-item {
    display: flex;
    padding: 10px;
    flex-direction: row;
    .item-label {
      width: 100px;
      text-align: right;
      line-height: 28px;
    }
    .item-input {

    }
  }
}

</style>
