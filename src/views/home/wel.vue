<template>
  <div>
    <div class="crm-home-page">
      <el-card class="summary" :body-style="{ padding: '0px' }">
        <div class="header">
          <div class="wrapper">
            <crm-title-tabs v-model="tabIndex" :data="tabsData" />
            <el-select v-model="value" class="type1" placeholder="请选择">
              <el-option
                v-for="item in options"
                :key="item.value"
                :label="item.label"
                :value="item.value"
              />
            </el-select>
            <el-select v-model="value" class="type2" placeholder="请选择">
              <el-option
                v-for="item in options"
                :key="item.value"
                :label="item.label"
                :value="item.value"
              />
            </el-select>
          </div>

        </div>
        <div class="content">
          <div v-show="tabIndex === 0" class="personal-data">
            <div class="today-contact-count">
              今日沟通量：20
            </div>

            <table>
              <tr>
                <td class="td-left">
                  <div class="td-content">
                    <div class="data">
                      <span class="number">20</span>
                      <span class="unit">单</span>
                    </div>
                    <div class="label">
                      本月销售额
                    </div>
                  </div>
                </td>
                <td class="lastCol td-right">
                  <div class="td-content">
                    <div class="data">
                      <span class="number">20</span>
                      <span class="unit">单</span>
                    </div>
                    <div class="label">
                      本月销售额
                    </div>
                  </div>
                </td>
              </tr>
              <tr class="lastrow">
                <td class="td-left">
                  <div class="td-content">
                    <div class="data">
                      <span class="number">20</span>
                      <span class="unit">单</span>
                    </div>
                    <div class="label">
                      本月销售额
                    </div>
                  </div>
                </td>
                <td class="lastCol td-right">
                  <div class="td-content">
                    <div class="data">
                      <span class="number">20</span>
                      <span class="unit">单</span>
                    </div>
                    <div class="label">
                      本月销售额
                    </div>
                  </div>
                </td>
              </tr>

            </table>
          </div>
          <div v-show="tabIndex !== 0" class="team-data">
            <div class="leader-avatar">
              <div class="text">
                Leader
              </div>
              <div class="leader-name">
                张珊珊
              </div>
            </div>

            <div class="members">
              <div v-for="i in 5" class="member-name">
                吕布
              </div>
              <div class="member-name">
                张飞
              </div>
            </div>
          </div>
          <div class="recently-data">
            <v-chart :options="recentlyDataOption" />
          </div>
          <div class="yearly-target sales-target">
            <div class="title">年度目标</div>
            <v-chart :options="yearlyTargetOptions" />
          </div>
          <div class="quarterly-target sales-target">
            <div class="title">年度目标</div>
            <v-chart :options="yearlyTargetOptions" />
          </div>
          <div class="monthly-target sales-target">
            <div class="title">年度目标</div>
            <v-chart :options="yearlyTargetOptions" />
          </div>
        </div>
      </el-card>
      <TableWrapper />
    </div>
  </div>
</template>

<script>
import CrmTitleTabs from '@/components/crmTitleTabs'
import ECharts from 'vue-echarts'

import 'echarts/lib/chart/line'
import 'echarts/lib/chart/pie'
import 'echarts/lib/component/legend'
import 'echarts/lib/component/title'
import 'echarts/lib/component/tooltip'
import 'echarts/lib/component/toolbox'
import 'echarts/lib/component/markPoint'
import 'echarts/lib/component/markLine'
import TableWrapper from './tableWrapper'

export default {
  name: 'Wel',
  components: {
    CrmTitleTabs,
    'v-chart': ECharts,
    TableWrapper
  },
  data() {
    return {
      tabsData: ['个人', '团队', '团队Ⅱ'],
      tabIndex: 1,
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
      }],
      value: '',
      recentlyDataOption: {
        xAxis: {
          type: 'category',
          data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        yAxis: {
          type: 'value'
        },
        series: [
          {
            data: [120, 200, 150, 80, 70, 110, 130],
            type: 'bar',
            showBackground: true,
            backgroundStyle: {
              color: 'rgba(180, 180, 180, 0.2)'
            }
          }
        ]
      },
      yearlyTargetOptions: {
        tooltip: {
          trigger: 'item'
        },
        // legend: {
        //   top: '5%',
        //   left: 'center'
        // },
        series: [
          {
            name: '销售额',
            type: 'pie',
            radius: ['30%', '90%'],
            avoidLabelOverlap: false,
            itemStyle: {
              borderRadius: 10,
              borderColor: '#fff',
              borderWidth: 2,
              normal: {
                color: function(colors) {
                  const colorList = [
                    '#67C23A',
                    '#FFBE44'
                  ]
                  return colorList[colors.dataIndex]
                }
              }
            },
            label: {
              show: false,
              position: 'center'
            },
            // emphasis: {
            //   label: {
            //     show: true,
            //     fontSize: '40',
            //     fontWeight: 'bold'
            //   }
            // },
            labelLine: {
              show: false
            },
            data: [
              { value: 80, name: '已完成' },
              { value: 20, name: '未完成' }
            ]
          }
        ]
      }
      // ***
      // 中间表格部分
      // ***

    }
  },
  computed: {
  },
  methods: {

  }
}
</script>

<style scoped="scoped" lang="scss">
  .crm-home-page {
    margin: 10px 16px;
  }

  .summary {
    border-radius: 10px;
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
      display: flex;
    }
  }

  /*/deep/.wrapper {
    .el-select {
      width: 304px;
    }

    .type1 {
      margin-left: auto;
      margin-right: 16px;
    }

    .el-input__inner {
      height: 42px;
    }

    !* 下面设置右侧按钮居中 *!
    .el-input__suffix {
      top: 13px;
    }

    .el-input__icon {
      line-height: inherit;
    }

    .el-input__suffix-inner {
      display: inline-block;
    }
  }*/

  .personal-data {
    //width: 268px;
    //height: 237px;
    background: #FFFFFF;
    box-shadow: 0px 0px 10px 1px rgba(27,101,185,0.1);
    border-radius: 10px;
    opacity: 1;
    margin: 12px 0 0 24px;
    padding: 16px;
    width: fit-content;
    height: fit-content;

    .today-contact-count {
      width: 236px;
      height: 34px;
      background: #3CA0F619;
      margin-bottom: 18px;
      font-size: 16px;
      line-height: 34px;
      font-weight: bold;
      color: #303133;
      text-align: center;
    }

    table{
      width: 236px;
      border-collapse: collapse;
      border: 0px solid #EBEEF5;
    }

    table {
      td {
        border-top: 0;
        border-right: 1px solid #EBEEF5;
        border-bottom: 1px solid #EBEEF5;
        border-left: 0;
        width: 50%;
        height: 73px;

        .td-content {
          width: 100%;
          height: 100%;
          display: flex;
          flex-direction: column;
          align-items: center;
          .data {
            display: flex;
            color: #1e90ff;
            .number {
              font-size: 24px;
              line-height: 24px;
              font-weight: bold;
            }

            .unit {
              margin-top: 16px;
              margin-left: 8px;
            }
          }

          .label {
            font-size: 14px;
            color: #303133;
            font-weight: 400;
            margin-top: 4px;
          }
        }
      }

      .lastrow {
        .td-content {
          justify-content: flex-end;
        }
      }

      .td-left {
        text-align: right;
        //.data {
        //  margin-right: 32px;
        //}
        //
        //.label {
        //  margin-right: 32px;
        //}
      }

      .td-right {
        text-align: left;
        //.data {
        //  margin-left: 32px;
        //}
        //
        //.label {
        //  margin-left: 32px;
        //}
      }
    }

    table tr.lastrow td {
      border-bottom: 0;
    }

    table tr td.lastCol {
      border-right: 0;
    }
  }

  .team-data {
    margin: 12px 0 0 24px;
    background: linear-gradient(180deg, #3CA0F626 0%, #3CA0F626 100%);
    border-radius: 10px 10px 10px 10px;
    padding: 24px;
    width: 220px;
    flex-shrink: 0;
    height: fit-content;
    .leader-avatar {
      width: 100px;
      height: 100px;
      background: linear-gradient(180deg, #3CA0F6 0%, #3B76EA 100%);
      opacity: 1;
      border-radius: 50px;
      font-size: 18px;
      font-weight: bold;
      color: #FFFFFF;
      margin: auto;

      .text {
        padding-top: 27px;
        text-align: center;
      }
    }

    .leader-name {
      width: 160px;
      height: 40px;
      background: #FFFFFF;
      box-shadow: 0px 0px 10px 1px rgba(27,101,185,0.1);
      border-radius: 20px 20px 20px 20px;
      opacity: 1;

      font-size: 20px;
      font-weight: bold;
      line-height: 40px;
      color: #3CA0F6;
      text-align: center;
      //transform: translateY(-40px);

      margin-top: 10px;
      margin-left: -30px;
    }

    .members {
      margin-top: 24px;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      .member-name {
        background: #3CA0F619;
        border-radius: 2px;
        width: fit-content;
        padding: 6px 12px;
        font-size: 14px;
        font-weight: 500;
        color: #303133;
        margin-left: 4px;
        margin-top: 4px;
      }
    }
  }

  .sales-target {
    display: flex;
    flex-direction: column;
    .title {
      margin: 28px 0 0 18px;
      font-size: 16px;
      font-weight: bold;
      color: #303133;
    }

    .echarts {
      width: 292px;
      height: 170px;
      margin-top: 25px;
      border-left: 1px solid #EBEEF5;
    }
  }

  .recently-data {
    .echarts {
      width: 292px;
      height: 170px;
      margin-top: 15px;
      border-left: 1px solid #EBEEF5;
    }
  }

  .yearly-target {

  }

</style>
