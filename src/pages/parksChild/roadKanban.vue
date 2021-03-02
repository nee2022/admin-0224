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
            <div class="firstBoxTop">道路总量</div>
            <div class="firstBoxBot">
              {{ resourceAndRecord.station_type_3_count }}
            </div>
          </div>
          <div class="rightBox">
            <div class="otherBoxs1">
              <div style="color: white;">泊位数</div>
              <div class="otherBoxsBot">
                <div class="otherBoxsBotBox">
                  <div class="otherNum">0</div>
                  <div class="otherWord">空闲</div>
                </div>
                <div class="otherBoxsBotBox">
                  <div class="otherNum">0</div>
                  <div class="otherWord">占用</div>
                </div>
                <div class="otherBoxsBotBox">
                  <el-progress
                    type="circle"
                    :percentage="0"
                    :stroke-width="10"
                    :width="60"
                    :format="
                      () => {
                        return 0;
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
                  <div class="otherNum">
                    {{ resourceAndRecord.charger_type_7_count_online }}
                  </div>
                  <div class="otherWord">在线</div>
                </div>
                <div class="otherBoxsBotBox">
                  <div class="otherNum">
                    {{ resourceAndRecord.charger_type_7_count }}
                  </div>
                  <div class="otherWord">总数</div>
                </div>
              </div>
            </div>
            <div class="otherBoxs3">
              <div style="color: white;">视频桩</div>
              <div class="otherBoxsBot">
                <div class="otherBoxsBotBox">
                  <div class="otherNum">
                    {{
                      resourceAndRecord.charger_type_10_count_online +
                        resourceAndRecord.charger_type_11_count_online
                    }}
                  </div>
                  <div class="otherWord">在线</div>
                </div>
                <div class="otherBoxsBotBox">
                  <div class="otherNum">
                    {{
                      resourceAndRecord.charger_type_10_count +
                        resourceAndRecord.charger_type_11_count
                    }}
                  </div>
                  <div class="otherWord">总数</div>
                </div>
              </div>
            </div>
            <div class="otherBoxs4">
              <div style="color: white;">巡检车</div>
              <div class="otherBoxsBot">
                <div class="otherBoxsBotBox">
                  <div class="otherNum">
                    {{ resourceAndRecord.charger_type_18_count_online }}
                  </div>
                  <div class="otherWord">在线</div>
                </div>
                <div class="otherBoxsBotBox">
                  <div class="otherNum">
                    {{ resourceAndRecord.charger_type_18_count }}
                  </div>
                  <div class="otherWord">总数</div>
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
            <div class="boxNum">{{ resourceAndRecord.pdr_count }}</div>
          </div>
          <div class="boxBoxs">
            <div class="boxWord">停车费</div>
            <div class="boxNum1">{{ resourceAndRecord.pdr_amount }}</div>
          </div>
          <div class="boxBoxs">
            <div class="boxWord">已缴</div>
            <div class="boxNum1">{{ resourceAndRecord.pdr_paid }}</div>
          </div>
          <div class="boxBoxs">
            <div class="boxWord">欠费</div>
            <div class="boxNum1">{{ resourceAndRecord.pdr_debts }}</div>
          </div>
          <div class="boxBoxs">
            <div class="boxWord">退款</div>
            <div class="boxNum1">{{ resourceAndRecord.pdr_refund }}</div>
          </div>
          <div class="boxBoxs">
            <div class="boxWord">优惠</div>
            <div class="boxNum1">0</div>
          </div>
        </div>
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
      resourceAndRecord: {},
      operationData: [],
      tableChangeInfo: {
        itemName: "日期",
        code: "AC5FF95637CF4B4294A6B650535F5531"
      },
      total: 1000,
      pagenum: 1,
      pagesize: 10
    };
  },
  created() {},
  mounted() {
    this.token = localStorage.getItem("token").replace(/\"/g, "");
    this.getResourceAndRecord();
  },
  methods: {
    getResourceAndRecord() {
      let url =
        "admin/api/report/FA201E10D5154499BA2C74FC0998F464" +
        "/?token=" +
        this.token +
        "&page=" +
        this.pagenum +
        "&row=" +
        this.pagesize;

      this.$axios.get(url).then(res => {
        if (res.status == 200) {
          this.resourceAndRecord = res.data.data[0];
        }
      });
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
  height: 2650px;
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
  width: 30%;
  height: 120px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  background: url(../../assets/images/boweix@2x.png) no-repeat;
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
