<template>
  <div class="road-right">
    <div class="UserAssets-right-top">
      <div class="user-left">
        <span class="user-word">道路停车</span>
      </div>
      <div class="users-right">
        <myhead></myhead>
      </div>
    </div>
    <div class="wulianBot">
      <div class="wulianBotBox">
        <div class="wulianBotBoxT">
          <div class="T_blue"></div>
          <span class="T_span">资源</span>
        </div>
        <div class="roadBot">
          <div class="firstBox">
            <div class="firstBoxTop">站点总量</div>
            <div class="firstBoxBot">9548</div>
          </div>
          <div class="rightBox">
            <div class="otherBoxs1">
              <div style="color: white;">泊位数</div>
              <div class="otherBoxsBot">
                <div class="otherBoxsBotBox">
                  <div class="otherNum">3430</div>
                  <div class="otherWord">空闲</div>
                </div>
                <div class="otherBoxsBotBox">
                  <div class="otherNum">3430</div>
                  <div class="otherWord">占用</div>
                </div>
                <div class="otherBoxsBotBox">
                  <el-progress
                    type="circle"
                    :percentage="25"
                    :stroke-width="10"
                    :width="60"
                    :format="
                      () => {
                        return 1;
                      }
                    "
                  ></el-progress>
                  <div class="otherWord">占用率</div>
                </div>
              </div>
            </div>
            <div class="otherBoxs2">
              <div style="color: white;">地磁</div>
              <div class="otherBoxsBot">
                <div class="otherBoxsBotBox">
                  <div class="otherNum">3430</div>
                  <div class="otherWord">空闲</div>
                </div>
                <div class="otherBoxsBotBox">
                  <div class="otherNum">8430</div>
                  <div class="otherWord">离线</div>
                </div>
              </div>
            </div>
            <div class="otherBoxs3">
              <div style="color: white;">视频桩</div>
              <div class="otherBoxsBot">
                <div class="otherBoxsBotBox">
                  <div class="otherNum">3430</div>
                  <div class="otherWord">空闲</div>
                </div>
                <div class="otherBoxsBotBox">
                  <div class="otherNum">8430</div>
                  <div class="otherWord">离线</div>
                </div>
              </div>
            </div>
            <div class="otherBoxs4">
              <div style="color: white;">巡检车</div>
              <div class="otherBoxsBot">
                <div class="otherBoxsBotBox">
                  <div class="otherNum">3430</div>
                  <div class="otherWord">空闲</div>
                </div>
                <div class="otherBoxsBotBox">
                  <div class="otherNum">8430</div>
                  <div class="otherWord">离线</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="wulianBotBox">
        <div class="wulianBotBoxT">
          <div class="T_blue"></div>
          <span class="T_span">订单</span>
        </div>
        <div class="ziyuanBox">
          <div class="boxBoxs">
            <div class="boxWord">订单数</div>
            <div class="boxNum">3420</div>
          </div>
          <div class="boxBoxs">
            <div class="boxWord">停车费</div>
            <div class="boxNum1">3420</div>
          </div>
          <div class="boxBoxs">
            <div class="boxWord">已缴</div>
            <div class="boxNum1">3420</div>
          </div>
          <div class="boxBoxs">
            <div class="boxWord">欠费</div>
            <div class="boxNum1">3420</div>
          </div>
          <div class="boxBoxs">
            <div class="boxWord">退款</div>
            <div class="boxNum1">3420</div>
          </div>
          <div class="boxBoxs">
            <div class="boxWord">优惠</div>
            <div class="boxNum1">3420</div>
          </div>
        </div>
      </div>
      <div class="wulianBotBox1">
        <div class="roadTopBox">
          <div
            style="display: flex;flex-direction: row;align-items: center;height: 50px;"
          >
            <div class="T_blue"></div>
            <span class="T_span">停车数据曲线</span>
          </div>
          <div class="dateR">
            <div class="dateBox3">
              <div
                class="blueBoxs"
                v-for="item in dateList"
                :class="{ BGactive: item.id == isActive }"
                @click="changeBg(item.id)"
              >
                {{ item.name }}
              </div>
            </div>
            <div class="dateSel">
              <template>
                <div class="block" v-show="isBg == 1">
                  <el-date-picker
                    v-model="value3"
                    type="daterange"
                    range-separator="至"
                    start-placeholder="开始日期"
                    end-placeholder="结束日期"
                    value-format="yyyyMMdd"
                    @change="chooseDate"
                  >
                  </el-date-picker>
                  <!-- <el-date-picker v-model="value1" type="date" placeholder="开始日期" value-format="yyyyMMdd" @change="chooseDate1">
									</el-date-picker>
									至
									<el-date-picker v-model="value2" type="date" placeholder="结束日期" value-format="yyyyMMdd" @change="chooseDate2">
									</el-date-picker> -->
                </div>
                <div class="block" v-show="isBg == 2">
                  <el-date-picker
                    v-model="value3"
                    type="monthrange"
                    range-separator="至"
                    start-placeholder="开始月份"
                    end-placeholder="结束月份"
                    value-format="yyyyMM"
                    @change="chooseDate"
                  >
                  </el-date-picker>
                </div>
                <div class="block" v-show="isBg == 3">
                  <el-date-picker
                    v-model="value1"
                    type="year"
                    placeholder="开始年份"
                    value-format="yyyy"
                    @change="chooseDate1"
                  >
                  </el-date-picker>
                  至
                  <el-date-picker
                    v-model="value2"
                    type="year"
                    placeholder="结束年份"
                    value-format="yyyy"
                    @change="chooseDate2"
                  >
                  </el-date-picker>
                </div>
              </template>
            </div>
            <div>
              <el-button
                type="primary"
                icon="el-icon-search"
                @click="searchData()"
                >查询</el-button
              >
            </div>
          </div>
        </div>
        <div class="charstBox1" id="myEcharts1"></div>
      </div>
      <div class="wulianBotBox1">
        <div class="roadTopBox">
          <div
            style="display: flex;flex-direction: row;align-items: center;height: 50px;"
          >
            <div class="T_blue"></div>
            <span class="T_span">停车场排名</span>
          </div>
          <div class="dateR2">
            <div class="dateBox">
              <div
                class="blueBoxs"
                v-for="item in day"
                :class="{ BGactive: item.id == isActive1 }"
                @click="changeBg1(item.id)"
              >
                {{ item.name }}
              </div>
            </div>
            <div class="dateBox1">
              <div
                class="blueBoxs1"
                v-for="item in shouList"
                :class="{ BGactive: item.id == isActive2 }"
                @click="changeBg2(item.id)"
              >
                {{ item.name }}
              </div>
            </div>
          </div>
        </div>
        <div class="charstBox1" id="myEcharts2"></div>
      </div>
      <div class="wulianBotBox1">
        <div class="roadTopBox">
          <div
            style="display: flex;flex-direction: row;align-items: center;height: 50px;"
          >
            <div class="T_blue"></div>
            <span class="T_span">运营商排名</span>
          </div>
          <div class="dateR2">
            <div class="dateBox">
              <div
                class="blueBoxs"
                v-for="item in day"
                :class="{ BGactive: item.id == isActive3 }"
                @click="changeBg3(item.id)"
              >
                {{ item.name }}
              </div>
            </div>
            <div class="dateBox1">
              <div
                class="blueBoxs1"
                v-for="item in shouList"
                :class="{ BGactive: item.id == isActive4 }"
                @click="changeBg4(item.id)"
              >
                {{ item.name }}
              </div>
            </div>
          </div>
        </div>
        <div class="charstBox1" id="myEcharts3"></div>
      </div>
      <div class="wulianBotBox1">
        <div class="roadTopBox">
          <div
            style="display: flex;flex-direction: row;align-items: center;height: 50px;"
          >
            <div class="T_blue"></div>
            <span class="T_span">欠费排名</span>
          </div>
          <div class="dateR2">
            <div class="dateBox">
              <div
                class="blueBoxs"
                v-for="item in day"
                :class="{ BGactive: item.id == isActive5 }"
                @click="changeBg5(item.id)"
              >
                {{ item.name }}
              </div>
            </div>
            <div class="dateBox1">
              <div
                class="blueBoxs1"
                v-for="item in shouList"
                :class="{ BGactive: item.id == isActive6 }"
                @click="changeBg6(item.id)"
              >
                {{ item.name }}
              </div>
            </div>
          </div>
        </div>
        <div class="charstBox1" id="myEcharts4"></div>
      </div>
      <div class="wulianBotBox1">
        <div class="roadTopBox">
          <div
            style="display: flex;flex-direction: row;align-items: center;height: 50px;"
          >
            <div class="T_blue"></div>
            <span class="T_span">收费员绩效排名</span>
          </div>
          <div class="dateR2">
            <div class="dateBox">
              <div
                class="blueBoxs"
                v-for="item in day"
                :class="{ BGactive: item.id == isActive7 }"
                @click="changeBg7(item.id)"
              >
                {{ item.name }}
              </div>
            </div>
            <div class="dateBox1">
              <div
                class="blueBoxs1"
                v-for="item in shouList"
                :class="{ BGactive: item.id == isActive8 }"
                @click="changeBg8(item.id)"
              >
                {{ item.name }}
              </div>
            </div>
          </div>
        </div>
        <div class="charstBox1" id="myEcharts5"></div>
      </div>
    </div>
  </div>
</template>

<script>
import myhead from "../../components/myhead.vue";
export default {
  components: {
    myhead
  },
  data() {
    return {
      total: 1000,
      pagenum: 1,
      pagesize: 10,
      isActive: 1,
      isActive1: 1,
      isActive2: 1,
      isActive3: 1,
      isActive4: 1,
      isActive5: 1,
      isActive6: 1,
      isActive7: 1,
      isActive8: 1,
      isBg: 1,
      isBg2: 1,
      value1: "",
      value2: "",
      value3: "",
      shouList: [
        {
          name: "收入",
          id: 1
        },
        {
          name: "取证率",
          id: 2
        }
      ],
      day: [
        {
          name: "今年",
          id: 1
        },
        {
          name: "本月",
          id: 2
        },
        {
          name: "今天",
          id: 3
        }
      ],
      dateList: [
        {
          name: "近一周",
          id: 1
        },
        {
          name: "近一月",
          id: 2
        },
        {
          name: "近一年",
          id: 3
        }
      ]
    };
  },
  created() {
    this.$nextTick(() => {
      this.drawChart1();
      this.drawChart2();
      this.drawChart3();
      this.drawChart4();
      this.drawChart5();
    });
  },
  methods: {
    changeBg(id) {
      this.isActive = id;
    },
    changeBg1(id) {
      this.isActive1 = id;
    },
    changeBg2(id) {
      this.isActive2 = id;
    },
    changeBg3(id) {
      this.isActive3 = id;
    },
    changeBg4(id) {
      this.isActive4 = id;
    },
    changeBg5(id) {
      this.isActive5 = id;
    },
    changeBg6(id) {
      this.isActive3 = id;
    },
    changeBg7(id) {
      this.isActive4 = id;
    },
    changeBg8(id) {
      this.isActive5 = id;
    },
    chooseDate1() {
      console.log(this.value1);
    },
    chooseDate() {
      console.log(this.value3);
      this.value1 = this.value3[0];
      this.value2 = this.value3[1];
      console.log(this.value1);
      console.log(this.value2);
    },
    chooseDate2() {
      console.log(this.value2);
    },
    drawChart1() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById("myEcharts1"));
      // 指定图表的配置项和数据
      var option = {
        tooltip: {
          trigger: "axis"
        },
        color: ["#ff7200", "#00cc57", "#238ae1"],
        grid: {},
        legend: {
          data: ["应收", "实收", "欠费"],
          orient: "horizontal", //垂直显示
          y: "bottom", //延Y轴居中
          x: "center", //居右显示
          itemGap: 100, //图例间隔
          textStyle: {
            fontSize: 16
          }
          // show: true,
          // borderWidth: 2,
          // shadowColor: 'rgba(0, 0, 0, 0.5)',
          // shadowBlur: 5,
          // borderRadius: 10,
          // padding: [20, 10],
        },
        xAxis: {
          data: [1, 2, 3, 4, 5],
          fontSize: 18
        },
        yAxis: {
          type: "value",
          name: "单位:金额"
        },
        series: [
          {
            name: "应收",
            type: "line",
            data: [2, 432, 54, 1, 4],
            smooth: true
          },
          {
            name: "实收",
            type: "line",
            data: [22, 452, 524, 11, 54],
            smooth: true
          },
          {
            name: "欠费",
            type: "line",
            data: [252, 432, 244, 1214, 412],
            smooth: true
          }
        ]
      };
      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    },

    drawChart2() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById("myEcharts2"));
      // 指定图表的配置项和数据
      var option = {
        tooltip: {
          show: true
        },
        xAxis: {
          type: "category",
          data: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
          axisLabel: {
            show: true,
            textStyle: {
              fontSize: 16
            }
          }
        },
        yAxis: {
          type: "value",
          name: "单位:元",
          axisLabel: {
            show: true,
            textStyle: {
              fontSize: 16
            }
          }
        },
        series: [
          {
            data: [2320, 1700, 3150, 2480, 4670, 1110, 3255, 6546, 2313, 4325],
            type: "bar",
            barWidth: "60",
            itemStyle: {
              normal: {
                color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  {
                    offset: 1,
                    color: "#9929ea"
                  },
                  {
                    offset: 0,
                    color: "#5808fb"
                  }
                ])
              }
            },
            label: {
              //label要加入normal才可生效,label即为x轴对应Y轴的值
              normal: {
                show: true,
                color: "#5808fb", //设置渐变时候控制不到颜色，只能通过全局textStyle来控制
                position: "top"
              }
            }
          }
        ]
      };
      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    },

    drawChart3() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById("myEcharts3"));
      // 指定图表的配置项和数据
      var option = {
        tooltip: {
          show: true
        },
        xAxis: {
          type: "category",
          data: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
          axisLabel: {
            show: true,
            textStyle: {
              fontSize: 16
            }
          }
        },
        yAxis: {
          type: "value",
          name: "单位:元",
          axisLabel: {
            show: true,
            textStyle: {
              fontSize: 16
            }
          }
        },
        series: [
          {
            data: [2320, 1700, 3150, 2480, 4670, 1110, 3255, 6546, 2313, 4325],
            type: "bar",
            barWidth: "60",
            itemStyle: {
              normal: {
                color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  {
                    offset: 1,
                    color: "#0bbafb"
                  },
                  {
                    offset: 0,
                    color: "#4285ec"
                  }
                ])
              }
            },
            label: {
              //label要加入normal才可生效,label即为x轴对应Y轴的值
              normal: {
                show: true,
                color: "#4285ec", //设置渐变时候控制不到颜色，只能通过全局textStyle来控制
                position: "top"
              }
            }
          }
        ]
      };
      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    },
    drawChart4() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById("myEcharts4"));
      // 指定图表的配置项和数据
      var option = {
        tooltip: {
          show: true
        },
        xAxis: {
          type: "category",
          data: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
          axisLabel: {
            show: true,
            textStyle: {
              fontSize: 16
            }
          }
        },
        yAxis: {
          type: "value",
          name: "单位:元",
          axisLabel: {
            show: true,
            textStyle: {
              fontSize: 16
            }
          }
        },
        series: [
          {
            data: [2320, 1700, 3150, 2480, 4670, 1110, 3255, 6546, 2313, 4325],
            type: "bar",
            barWidth: "60",
            itemStyle: {
              normal: {
                color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  {
                    offset: 1,
                    color: "#84f5de"
                  },
                  {
                    offset: 0,
                    color: "#4cc5f8"
                  }
                ])
              }
            },
            label: {
              //label要加入normal才可生效,label即为x轴对应Y轴的值
              normal: {
                show: true,
                color: "#4cc5f8", //设置渐变时候控制不到颜色，只能通过全局textStyle来控制
                position: "top"
              }
            }
          }
        ]
      };
      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    },
    drawChart5() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById("myEcharts5"));
      // 指定图表的配置项和数据
      var option = {
        tooltip: {
          show: true
        },
        xAxis: {
          type: "category",
          data: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
          axisLabel: {
            show: true,
            textStyle: {
              fontSize: 16
            }
          }
        },
        yAxis: {
          type: "value",
          name: "单位:元",
          axisLabel: {
            show: true,
            textStyle: {
              fontSize: 16
            }
          }
        },
        series: [
          {
            data: [2320, 1700, 3150, 2480, 4670, 1110, 3255, 6546, 2313, 4325],
            type: "bar",
            barWidth: "60",
            itemStyle: {
              normal: {
                color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  {
                    offset: 1,
                    color: "#015eea"
                  },
                  {
                    offset: 0,
                    color: "#00c0fa"
                  }
                ])
              }
            },
            label: {
              //label要加入normal才可生效,label即为x轴对应Y轴的值
              normal: {
                show: true,
                color: "#00c0fa", //设置渐变时候控制不到颜色，只能通过全局textStyle来控制
                position: "top"
              }
            }
          }
        ]
      };
      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    }
  }
};
</script>

<style scoped="scoped">
.road-right {
  display: flex;
  flex: 1;
  flex-direction: column;
  background-color: white;
  border-top-left-radius: 50px;
  border-bottom-left-radius: 50px;
  height: 3150px;
}

.BGactive {
  background-color: #0000ff;
  color: white;
  border-radius: 10px;
}

.charstBox1 {
  width: 100%;
  height: 85%;
}

.block {
  width: 300px;
  border: solid 1px #1e69fe;
  border-radius: 5px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.dateR >>> .el-button--primary {
  color: #fff;
  background-color: #0000ff;
  border-color: #0000ff;
  height: 35px;
  width: 80px;
}

.dateSel >>> .el-input__inner {
  height: 35px;
  border: none;
  text-align: center;
}

.dateSel >>> .el-date-editor.el-input {
  width: 100px;
}

.blueBoxs {
  width: 33.333%;
  text-align: center;
  line-height: 30px;
}

.blueBoxs1 {
  width: 50%;
  text-align: center;
  line-height: 30px;
}

.dateR {
  width: 850px;
  height: 50px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.dateR2 {
  width: 550px;
  height: 50px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.dateBox {
  width: 55%;
  height: 30px;
  display: flex;
  flex-direction: row;
  border: solid 1px #0000ff;
  border-radius: 10px;
  cursor: pointer;
}

.dateBox3 {
  width: 420px;
  height: 30px;
  display: flex;
  flex-direction: row;
  border: solid 1px #0000ff;
  border-radius: 10px;
  cursor: pointer;
}

.dateBox1 {
  width: 40%;
  height: 30px;
  display: flex;
  flex-direction: row;
  border: solid 1px #0000ff;
  border-radius: 10px;
  cursor: pointer;
}

.jindut {
  flex: 1;
}

.jindut1 {
  flex: 1;
}

.jindut2 {
  flex: 1;
}

.jindut1 >>> .el-progress-bar__inner {
  border-radius: 5px;
  background-color: ;
  background-image: linear-gradient(93deg, #4facfe 0%, #00f2fe 100%);
}

.jindut1 >>> .el-progress-bar__outer {
  border-radius: 5px;
  background-color: #ddecfb;
}

.jindut2 >>> .el-progress-bar__inner {
  border-radius: 5px;
  background-color: ;
  background-image: linear-gradient(93deg, #85f4bb 0%, #8cd9e8 100%);
}

.jindut2 >>> .el-progress-bar__outer {
  border-radius: 5px;
  background-color: #ddecfb;
}

.jindut >>> .el-progress-bar__inner {
  border-radius: 5px;
  background-color: ;
  background-image: linear-gradient(88deg, #3fbbfe 0%, #a541ff 100%);
}

.jindut >>> .el-progress-bar__outer {
  border-radius: 5px;
  background-color: #ddecfb;
}

.tingchechangName {
  width: 12%;
  text-align: center;
}

.roadConBox {
  width: 100%;
  height: 370px;
  display: flex;
  flex-direction: column;
}

.jindutiaoBox {
  width: 100%;
  height: 10%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.roadBotBox {
  display: flex;
  flex: 1;
  flex-direction: row;
  justify-content: flex-end;
  align-items: center;
}

.boxNum {
  font-size: 30px;
  font-weight: 600;
  color: #0000ff;
}

.roadTopBox {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 100%;
}

.boxNum1 {
  font-size: 30px;
  font-weight: 600;
  color: #f8701e;
}

.boxBoxs {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  height: 70px;
}

.ziyuanBox {
  width: 100%;
  height: 100%;
  justify-content: space-around;
  display: flex;
  flex-direction: row;
  align-items: center;
}

.boxBoxs {
  width: 15%;
}

.otherWord {
  height: 20px;
  width: 50px;
  color: white;
  border-radius: 10px;
  text-align: center;
  line-height: 20px;
}

.otherBoxsBot {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.otherNum {
  color: white;
  font-size: 30px;
  font-weight: 600;
}

.otherBoxsBotBox {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  width: 45%;
  align-items: center;
  height: 75px;
}

.rightBox {
  display: flex;
  flex-direction: row;
  width: 85%;
  justify-content: space-between;
}

.otherBoxs1 {
  width: 25%;
  height: 120px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  background: url(../../assets/images/bowei.png) no-repeat;
  background-size: 100% 100%;
}

.otherBoxs2 {
  width: 22%;
  height: 120px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  background: url(../../assets/images/diciB.png) no-repeat;
  background-size: 100% 100%;
}

.otherBoxs3 {
  width: 22%;
  height: 120px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  background: url(../../assets/images/shexiang.png) no-repeat;
  background-size: 100% 100%;
}

.otherBoxs4 {
  width: 22%;
  height: 120px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  background: url(../../assets/images/cheliang.png) no-repeat;
  background-size: 100% 100%;
}

.firstBoxTop {
  height: 30px;
  line-height: 30px;
  color: white;
}

.firstBoxBot {
  font-size: 40px;
  color: white;
  font-weight: 600;
}

.firstBox {
  width: 120px;
  height: 120px;
  background: url(../../assets/images/frist.png);
  display: flex;
  flex-direction: column;
  border-radius: 10px;
  align-items: center;
  justify-content: center;
}

.roadBot {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
}

.wulianBotBoxBot {
  width: 100%;
  height: 270px;
  display: flex;
  flex-direction: row;
}

.CwordBox {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 50px;
  align-items: center;
  margin: 0 auto;
}

.CwordBox1 {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 65px;
  align-items: center;
  margin: 0 auto;
}

.Cnum {
  font-size: 30px;
  color: #0000ff;
  font-weight: 600;
}

.quan {
  width: 15px;
  height: 15px;
  border-radius: 50%;
}

.green {
  background-color: #35fb3e;
}

.gray {
  background-color: #a0a0a0;
}

.blue {
  background-color: #0000ff;
}

.orange {
  background-color: #f8701e;
}

.red {
  background-color: #fb0c28;
}

.purple {
  background-color: #ab24f8;
}

.CnumBox {
  display: flex;
  flex-direction: column;
  height: 50px;
  justify-content: space-between;
}

.conCon {
  display: flex;
  flex: 1;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.conRight {
  width: 30%;
  height: 100%;
}

.Ltitle {
  font-size: 14px;
  width: 60%;
  margin: 0 auto;
}

.Lnum {
  font-size: 50px;
  height: 140px;
  color: #0000ff;
  font-weight: 600;
}

.conLeft {
  display: flex;
  flex-direction: column;
  width: 20%;
  height: 100%;
  align-items: center;
  justify-content: space-around;
}

.wulianBotBoxT {
  display: flex;
  flex-direction: row;
  align-items: center;
}

.T_span {
  font-size: 18px;
  margin-left: 5px;
}

.wulianBotBox {
  width: 100%;
  height: 200px;
}

.wulianBotBox1 {
  width: 100%;
  height: 500px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-top: 50px;
}

.T_blue {
  width: 5px;
  height: 15px;
  background-color: #0000ff;
}

.wulianBot {
  width: 95%;
  margin: 0 auto;
  height: 85%;
  display: flex;
  flex-direction: column;
}

.UserAssets-right-top {
  display: flex;
  flex-direction: row;
  width: 95%;
  margin: 20px auto;
  margin-top: 40px;
}

.user-left {
  flex: 1;
}

.users-right {
  width: 150px;
}

.user-word {
  width: 47px;
  height: 23px;
  font-family: PingFangSC-Regular;
  font-size: 24px;
  font-weight: normal;
  font-stretch: normal;
  line-height: 24px;
  letter-spacing: 1px;
  color: #000000;
}
</style>
