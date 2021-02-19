<template>
  <div>
    <el-form
      ref="formZlywB"
      :model="formZlywB"
      label-width="180px"
      label-position="left"
      :inline="true"
    >
 
             <!-- 治疗药物(B非心血管药物) -->

        <el-row>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="1. 非甾体类抗炎药" class="item">
                <el-select
                  v-model="formZlywB.zlyw_b['非甾体类抗炎药']"
                  placeholder="请选择非甾体类抗炎药"
                >
                  <el-option
                    v-for="item in base_selarr"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
        </el-row>

        <el-row>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="2. 抗糖尿病药物" class="item">
                <el-select
                  v-model="formZlywB.zlyw_b['抗糖尿病药物']['是否服用']"
                  placeholder="请选择抗糖尿病药物"
                >
                  <el-option
                    v-for="item in base_selarr"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="2.1 恩格列净(mg/d)" class="item">
                <el-input
                  v-model="formZlywB.zlyw_b['抗糖尿病药物']['恩格列净(mg/d)']"
                  placeholder="请输入恩格列净(mg/d)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="2.2 恩格列净(mg/d)" class="item">
                <el-input
                  v-model="formZlywB.zlyw_b['抗糖尿病药物']['达格列净(mg/d)']"
                  placeholder="请输入达格列净(mg/d)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
        </el-row>

        <el-row>
            <el-col :span="8">
            <div class="grid-content">
                <el-form-item label="3. 抗抑郁药" class="item">
                <el-select
                    v-model="formZlywB.zlyw_b['抗抑郁药']"
                    placeholder="请选择抗抑郁药"
                >
                    <el-option
                    v-for="item in base_selarr"
                    :key="item"
                    :value="item"
                    ></el-option>
                </el-select>
                </el-form-item>
            </div>
            </el-col>
            <el-col :span="8">
            <div class="grid-content">
                <el-form-item label="4. 秋水仙碱" class="item">
                <el-select
                    v-model="formZlywB.zlyw_b['秋水仙碱']"
                    placeholder="请选择秋水仙碱"
                >
                    <el-option
                    v-for="item in base_selarr"
                    :key="item"
                    :value="item"
                    ></el-option>
                </el-select>
                </el-form-item>
            </div>
            </el-col>
            <el-col :span="8">
            <div class="grid-content">
                <el-form-item label="5. 甲状腺激素替代治疗" class="item">
                <el-select
                    v-model="formZlywB.zlyw_b['甲状腺激素替代治疗']"
                    placeholder="请选择甲状腺激素替代治疗"
                >
                    <el-option
                    v-for="item in base_selarr"
                    :key="item"
                    :value="item"
                    ></el-option>
                </el-select>
                </el-form-item>
            </div>
            </el-col>
            <el-col :span="8">
            <div class="grid-content">
                <el-form-item label="6. 参加随机对照临床研究" class="item">
                <el-select
                    v-model="formZlywB.zlyw_b['是否参加随机对照临床研究']"
                    placeholder="请选择是否参加随机对照临床研究"
                >
                    <el-option
                    v-for="item in base_selarr"
                    :key="item"
                    :value="item"
                    ></el-option>
                </el-select>
                </el-form-item>
            </div>
            </el-col>
        </el-row>

      <!-- <el-tag style="margin-bottom: 10px" type="danger"
        >* 4. 坐位动脉血压输入：收缩压/舒张压，*/* mmHg！</el-tag
      >
      <br />
      <el-tag style="margin-bottom: 10px" type="danger"
        >* 8. 颈静脉压升高体征即：颈静脉充盈！</el-tag
      >
      <br /> -->
      <el-form-item>
        <el-button type="primary" @click="submitForm('formZlywB')"
          >保存</el-button
        >
        <el-button @click="resetForm()">重置</el-button>

      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "RecordZlywB",
  props: ["record_id"],
  data() {
    return {
      activeNames: "sqlllj",
      activeAdd: "add_first",
      base_selarr: ["是", "否"],
      extend_selarr: ["是", "否", "未知"],
      extend_selarr2: ["是", "否", "不明确"],
      tzbh: ["增加*kg", "减轻*kg", "无变化"],
      gjjmhlz: ["阳性", "阴性"],
      pfsd: ["湿", "干", "正常"],
      reason_a: [
        "禁忌",
        "不耐受",
        "患者要求",
        "不需要或无适应症",
        "已应用ARNI类药物",
        "已应用ARB类药物",
        "已应用ACEI类药物",
        "其它(请填写)",
      ],
      reason_b: [
        "血管性水肿",
        "肾动脉狭窄",
        "高血钾",
        "肾功能恶化",
        "咳嗽",
        "妊娠",
        "低血压",
        "其它(请填写)",
      ],
      formZlywB: {
        record_id: "",
        name: "",
        zlyw_b: {
          非甾体类抗炎药: "",
          抗糖尿病药物: {
            是否服用: "",
            "恩格列净(mg/d)": "",
            "达格列净(mg/d)": "",
          },
          抗抑郁药: "",
          秋水仙碱: "",
          甲状腺激素替代治疗: "",
          是否参加随机对照临床研究: "",
        },
      },
      template_data: {
        治疗药物A: {
          初步原因: [],
          具体症状: [],
          ACEI: {
            药物名称: ["贝那普利", "培哚普利", "依那普利", "其它"],
          },
          ARNI: {
            药物名称: ["沙库巴曲缬沙坦钠", "其它"],
          },
        },
      },
    };
  },
  methods: {
    resetForm() {
        this.formZlywB.zlyw_b["非甾体类抗炎药"] = null;
        this.formZlywB.zlyw_b["抗抑郁药"] = null;
        this.formZlywB.zlyw_b["秋水仙碱"] = null;
        this.formZlywB.zlyw_b["甲状腺激素替代治疗"] = null;
        this.formZlywB.zlyw_b["是否参加随机对照临床研究"] = null;
        this.formZlywB.zlyw_b["抗糖尿病药物"]["是否服用"]  = null;
        this.formZlywB.zlyw_b["抗糖尿病药物"]["恩格列净(mg/d)"]  = null;
        this.formZlywB.zlyw_b["抗糖尿病药物"]["达格列净(mg/d)"]  = null;
    },
    initformZlywB() {},
    loadZlywBData() {
      console.log("------loadZlywBData-------");
      this.resetForm();
      let record_id = this.record_id;
      // 读取数据
      this.getRequest("/visit/record/" + record_id).then((resp) => {
      
        console.log("------resp-------", resp);
        if (resp.zlyw_b) {
            console.log("------resp.zlyw_a-------", resp.zlyw_b);
          this.formZlywB.zlyw_b["非甾体类抗炎药"]  = JSON.parse(resp.zlyw_b)["非甾体类抗炎药"];
          this.formZlywB.zlyw_b["抗糖尿病药物"]["是否服用"]  = JSON.parse(resp.zlyw_b)["抗糖尿病药物"]["是否服用"];
          this.formZlywB.zlyw_b["抗糖尿病药物"]["恩格列净(mg/d)"]  = JSON.parse(resp.zlyw_b)["抗糖尿病药物"]["恩格列净(mg/d)"];
          this.formZlywB.zlyw_b["抗糖尿病药物"]["达格列净(mg/d)"]  = JSON.parse(resp.zlyw_b)["抗糖尿病药物"]["达格列净(mg/d)"];
          this.formZlywB.zlyw_b["抗抑郁药"]  = JSON.parse(resp.zlyw_b)["抗抑郁药"];
          this.formZlywB.zlyw_b["秋水仙碱"]  = JSON.parse(resp.zlyw_b)["秋水仙碱"];
          this.formZlywB.zlyw_b["甲状腺激素替代治疗"]  = JSON.parse(resp.zlyw_b)["甲状腺激素替代治疗"];
          this.formZlywB.zlyw_b["是否参加随机对照临床研究"]  = JSON.parse(resp.zlyw_b)["是否参加随机对照临床研究"];
          
        }
      });
    },
    submitForm() {
      this.formZlywB.record_id = this.record_id;
      var formData = JSON.stringify(this.formZlywB);
      console.log("this.formZlywB", this.formZlywB);
      this.putRequest("/visit/record/zlywB/", this.formZlywB).then((resp) => {
        if (resp) {
          this.loadZlywAData();
        }
      });
    },
    createFilter(curArr, queryString) {
      return (curArr) => {
        return curArr.toLowerCase().indexOf(queryString.toLowerCase()) === 0;
      };
    },
 // ACEI药物名称
    queryACEIywmcSearch(queryString, cb) {
      var querydata = this.template_data.治疗药物A.ACEI.药物名称;
      var results = queryString
        ? querydata.filter(this.createFilter(querydata, queryString))
        : querydata;
      var resultArr = [];
      for (let item of results) {
        resultArr.push({ value: item });
      }
      cb(resultArr);
    },
    // ARNI药物名称
    queryARNIywmcSearch(queryString, cb) {
      var querydata = this.template_data.治疗药物A.ARNI.药物名称;
      var results = queryString
        ? querydata.filter(this.createFilter(querydata, queryString))
        : querydata;
      var resultArr = [];
      for (let item of results) {
        resultArr.push({ value: item });
      }
      cb(resultArr);
    },
    // 原因A
    queryReasonASearch(queryString, cb) {
      var reason_a = this.reason_a;
      var results = queryString
        ? reason_a.filter(this.createFilter(reason_a, queryString))
        : reason_a;
      var resultArr = [];
      for (let item of results) {
        resultArr.push({ value: item });
      }
      cb(resultArr);
    },
  },
  mounted() {
    // 初始化数组
    this.loadZlywBData();
  },
  watch: {
    record_id: function (newData, oldData) {},
  },
};
</script>