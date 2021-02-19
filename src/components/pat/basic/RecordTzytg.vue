<template>
  <div>
    <el-form
      ref="formTzytg"
      :model="formTzytg"
      label-width="180px"
      label-position="left"
      :inline="true"
    >
      <!-- 体格检查与生命体征 -->
      <el-row>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="1.体重(kg)" class="item">
              <el-input
                v-model="formTzytg.tzytg['体重(kg)']"
                placeholder="请输入体重(kg)"
                maxlength="4"
              ></el-input>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="2.体重变化" class="item">
              <el-autocomplete
                popper-class="my-autocomplete"
                v-model="formTzytg.tzytg['体重变化']"
                :fetch-suggestions="queryTzbhSearch"
                placeholder="请输入体重变化"
              >
                <i class="el-icon-edit el-input__icon" slot="suffix"></i>
                <template slot-scope="props">
                  <div class="name">{{ props.item.value }}</div>
                  <!-- <span class="addr">{{ props.item.address }}</span> -->
                </template>
              </el-autocomplete>
            </el-form-item>
          </div>
        </el-col>

        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="3.体重指数" class="item">
              <el-input
                v-model="formTzytg.tzytg['体重指数']"
                placeholder="请输入体重指数"
                maxlength="4"
              ></el-input>
            </el-form-item>
          </div>
        </el-col>

        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="4.坐位动脉血压*/*mmHg" class="item">
              <el-input
                v-model="formTzytg.tzytg['坐位动脉血压']"
                placeholder="请输入坐位动脉血压/mmHg"
                maxlength="4"
              ></el-input>
            </el-form-item>
          </div>
        </el-col>

        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="5.静息心率(次/分)" class="item">
              <el-input
                v-model="formTzytg.tzytg['静息心率(次/分)']"
                placeholder="请输入静息心率(次/分)"
                maxlength="4"
              ></el-input>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="6.外周血氧饱和度(%)" class="item">
              <el-input
                v-model="formTzytg.tzytg['外周血氧饱和度(%)']"
                placeholder="请输入外周血氧饱和度(%)"
                maxlength="4"
              ></el-input>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="7.肺咯音" class="item">
              <el-select
                v-model="formTzytg.tzytg['肺咯音']"
                placeholder="请选择是否"
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
            <el-form-item label="8. 颈静脉压升高体征" class="item">
              <el-select
                v-model="formTzytg.tzytg['颈静脉压升高体征']"
                placeholder="请选择是否"
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
            <el-form-item label="9. 外周性水肿" class="item">
              <el-select
                v-model="formTzytg.tzytg['外周性水肿']"
                placeholder="请选择是否"
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
            <el-form-item label="10. 第三心音" class="item">
              <el-select
                v-model="formTzytg.tzytg['第三心音']"
                placeholder="请选择是否"
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
            <el-form-item label="11. 外周滴灌注体征" class="item">
              <el-select
                v-model="formTzytg.tzytg['外周滴灌注体征']"
                placeholder="请选择是否"
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
            <el-form-item label="12. 肝颈静脉回流征" class="item">
              <el-select
                v-model="formTzytg.tzytg['肝颈静脉回流征']"
                placeholder="请选择肝颈静脉回流征"
              >
                <el-option
                  v-for="item in gjjmhlz"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="13. 皮肤湿度" class="item">
              <el-select
                v-model="formTzytg.tzytg['皮肤湿度']"
                placeholder="请选择皮肤湿度"
              >
                <el-option
                  v-for="item in pfsd"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
      </el-row>

      <el-tag style="margin-bottom: 10px" type="danger"
        >* 4. 坐位动脉血压输入：收缩压/舒张压，*/* mmHg！</el-tag
      >
      <br />
      <el-tag style="margin-bottom: 10px" type="danger"
        >* 8. 颈静脉压升高体征即：颈静脉充盈！</el-tag
      >
      <br />
      <el-form-item>
        <el-button type="primary" @click="submitForm('formTzytg')"
          >保存</el-button
        >
        <el-button @click="resetForm()">重置</el-button>
        <!-- <el-button @click="initformTzytg()">初始化</el-button> -->
        <!-- <el-button @click="loadZzData()">读取数据</el-button> -->
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "RecordTzytg",
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
      formTzytg: {
        record_id: "",
        name: "",
        tzytg: {
          "体重(kg)": "",
          "体重变化(kg)": "",
          体重指数: "",
          坐位动脉血压: "",
          "静息心率(次/分)": "",
          "外周血氧饱和度(%)": "",
          肺咯音: "",
          颈静脉压升高体征: "",
          外周性水肿: "",
          第三心音: "",
          外周滴灌注体征: "",
          肝颈静脉回流征: "",
          皮肤湿度: "",
        },
      },
    };
  },
  methods: {
    resetForm() {
      // console.log("reset:");
      this.formTzytg.tzytg["体重(kg)"] = null;
      this.formTzytg.tzytg["体重变化(kg)"] = null;
      this.formTzytg.tzytg["体重指数"] = null;
      this.formTzytg.tzytg["坐位动脉血压"] = null;
      this.formTzytg.tzytg["静息心率(次/分)"] = null;
      this.formTzytg.tzytg["外周血氧饱和度(%)"] = null;
      this.formTzytg.tzytg["肺咯音"] = null;
      this.formTzytg.tzytg["颈静脉压升高体征"] = null;
      this.formTzytg.tzytg["外周性水肿"] = null;
      this.formTzytg.tzytg["第三心音"] = null;
      this.formTzytg.tzytg["外周滴灌注体征"] = null;
      this.formTzytg.tzytg["肝颈静脉回流征"] = null;
      this.formTzytg.tzytg["皮肤湿度"] = null;
    },
    initformTzytg() {},
    loadTzytgData() {
      console.log("------loadTzytgData-------");
      this.resetForm();
      let record_id = this.record_id;
      // 读取数据
      this.getRequest("/visit/record/" + record_id).then((resp) => {
        if (resp.tzytg) {
          // console.log("resp", resp);
          this.formTzytg.tzytg["体重(kg)"] = JSON.parse(resp.tzytg)["体重(kg)"];
          this.formTzytg.tzytg["体重变化(kg)"] = JSON.parse(resp.tzytg)[
            "体重变化(kg)"
          ];
          this.formTzytg.tzytg["体重指数"] = JSON.parse(resp.tzytg)["体重指数"];
          this.formTzytg.tzytg["坐位动脉血压"] = JSON.parse(resp.tzytg)[
            "坐位动脉血压"
          ];
          this.formTzytg.tzytg["静息心率(次/分)"] = JSON.parse(resp.tzytg)[
            "静息心率(次/分)"
          ];
          this.formTzytg.tzytg["外周血氧饱和度(%)"] = JSON.parse(resp.tzytg)[
            "外周血氧饱和度(%)"
          ];
          this.formTzytg.tzytg["肺咯音"] = JSON.parse(resp.tzytg)["肺咯音"];
          this.formTzytg.tzytg["颈静脉压升高体征"] = JSON.parse(resp.tzytg)[
            "颈静脉压升高体征"
          ];
          this.formTzytg.tzytg["外周性水肿"] = JSON.parse(resp.tzytg)[
            "外周性水肿"
          ];
          this.formTzytg.tzytg["第三心音"] = JSON.parse(resp.tzytg)["第三心音"];
          this.formTzytg.tzytg["外周滴灌注体征"] = JSON.parse(resp.tzytg)[
            "外周滴灌注体征"
          ];
          this.formTzytg.tzytg["肝颈静脉回流征"] = JSON.parse(resp.tzytg)[
            "肝颈静脉回流征"
          ];
          this.formTzytg.tzytg["皮肤湿度"] = JSON.parse(resp.tzytg)["皮肤湿度"];
        }
      });
    },
    submitForm() {
      this.formTzytg.record_id = this.record_id;
      var formData = JSON.stringify(this.formTzytg);
      console.log("this.formTzytg", this.formTzytg);
      this.putRequest("/visit/record/tzytg/", this.formTzytg).then((resp) => {
        if (resp) {
          this.loadTzytgData();
        }
      });
    },
    createFilter(curArr, queryString) {
      return (curArr) => {
        return curArr.toLowerCase().indexOf(queryString.toLowerCase()) === 0;
      };
    },
    //体重变化
    queryTzbhSearch(queryString, cb) {
      var tzbh = this.tzbh;
      var results = queryString
        ? tzbh.filter(this.createFilter(tzbh, queryString))
        : tzbh;
      var resultArr = [];
      for (let item of results) {
        resultArr.push({ value: item });
      }
      cb(resultArr);
    },
  },
  mounted() {
    // 初始化数组
    this.loadTzytgData();
  },
  watch: {
    record_id: function (newData, oldData) {},
  },
};
</script>