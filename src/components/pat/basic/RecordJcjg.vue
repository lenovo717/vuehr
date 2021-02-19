<template>
  <div>
    <el-form
      ref="formJcjg"
      :model="formJcjg"
      label-width="180px"
      label-position="left"
      :inline="true"
    >
      <!-- 检测结果 -->
      <el-row>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="1.空腹血糖(mmol/l)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['空腹血糖(mmol/l)']"
                  placeholder="请输入空腹血糖(mmol/l)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="2.HbA1c(%)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['HbA1c(%)']"
                  placeholder="请输入HbA1c(%)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="3.血清肌酐(mmol/l)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['血清肌酐(mmol/l)']"
                  placeholder="请输入血清肌酐(mmol/l)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="4.血红蛋白(mmol/l)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['血红蛋白(mmol/l)']"
                  placeholder="请输入血红蛋白(mmol/l)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="5.钠(mmol/l)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['钠(mmol/l)']"
                  placeholder="请输入钠(mmol/l)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="6.钾(mmol/l)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['钾(mmol/l)']"
                  placeholder="请输入钾(mmol/l)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="7.1 总胆固醇(mmol/l)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['总胆固醇(mmol/l)']"
                  placeholder="请输入总胆固醇(mmol/l)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="7.2 低密度脂蛋白(mmol/l)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['低密度脂蛋白(mmol/l)']"
                  placeholder="请输入低密度脂蛋白(mmol/l)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="8. 尿酸(mmol/l)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['尿酸(mmol/l)']"
                  placeholder="请输入尿酸(mmol/l)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="9. BNP(pg/ml)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['BNP(pg/ml)']"
                  placeholder="请输入BNP(pg/ml)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="10. NT-proBNP(pg/ml)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['NT-proBNP(pg/ml)']"
                  placeholder="请输入NT-proBNP(pg/ml)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="11. 同型半胱氨酸(mmol/l)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['同型半胱氨酸(mmol/l)']"
                  placeholder="请输入同型半胱氨酸(mmol/l)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="12. C反应蛋白" class="item">
                <el-input
                  v-model="formJcjg.jcjg['C反应蛋白']"
                  placeholder="请输入C反应蛋白"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="13. 铁蛋白(血清蛋白mg/l)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['铁蛋白(血清蛋白mg/l)']"
                  placeholder="请输入铁蛋白(血清蛋白mg/l)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
        </el-row>
        <!-- 14. 心电图是否检测 -->
        <el-row>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="14. 心电图是否检测" class="item">
                <el-select
                  v-model="formJcjg.jcjg['心电图']['是否检测过']"
                  placeholder="请选择是否检测"
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
              <el-form-item label="心电图日期" class="item" prop="心电图日期">
                <el-date-picker
                  v-model="formJcjg.jcjg['心电图']['心电图内容']['心电图日期']"
                  type="date"
                  placeholder="选择日期"
                ></el-date-picker>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="心率(次/分)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['心电图']['心电图内容']['心率(次/分)']"
                  placeholder="心率(次/分)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="心电图节律" class="item">
                <el-select
                  v-model="formJcjg.jcjg['心电图']['心电图内容']['心电图节律']"
                  placeholder="请选择心电图节律"
                >
                  <el-option
                    v-for="item in xdtjl"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="左束支传导阻滞" class="item">
                <el-select
                  v-model="
                    formJcjg.jcjg['心电图']['心电图内容']['左束支传导阻滞']
                  "
                  placeholder="请选择是否左束支传导阻滞"
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
              <el-form-item label="QRS时限(ms)" class="item">
                <el-input
                  v-model="formJcjg.jcjg['心电图']['心电图内容']['QRS时限(ms)']"
                  placeholder="QRS时限(ms)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
        </el-row>
        <!-- 15. 超声心动图(近12月内) -->
        <el-row>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="15. 超声心动图(近12月内)" class="item">
                <el-select
                  v-model="formJcjg.jcjg['超声心动图(近12月内)']['是否检测过']"
                  placeholder="请选择是否检测"
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
              <el-form-item label="超声心动图日期" class="item" prop="日期">
                <el-date-picker
                  v-model="
                    formJcjg.jcjg['超声心动图(近12月内)']['超声心动图内容'][
                      '日期'
                    ]
                  "
                  type="date"
                  placeholder="选择日期"
                ></el-date-picker>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="射血分数(%)" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['超声心动图(近12月内)']['超声心动图内容'][
                      '射血分数(%)'
                    ]
                  "
                  placeholder="射血分数(%)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="左心室舒张末期内径(mm)" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['超声心动图(近12月内)']['超声心动图内容'][
                      '左心室舒张末期内径(mm)'
                    ]
                  "
                  placeholder="左心室舒张末期内径(mm)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="左心房舒张末期内径(mm)" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['超声心动图(近12月内)']['超声心动图内容'][
                      '左心房舒张末期内径(mm)'
                    ]
                  "
                  placeholder="左心房舒张末期内径(mm)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="肺静脉血流图" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['超声心动图(近12月内)']['超声心动图内容'][
                      '肺静脉血流图'
                    ]
                  "
                  placeholder="肺静脉血流图"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="E/A" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['超声心动图(近12月内)']['超声心动图内容'][
                      'E/A'
                    ]
                  "
                  placeholder="E/A"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="E/e" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['超声心动图(近12月内)']['超声心动图内容'][
                      'E/e'
                    ]
                  "
                  placeholder="E/e"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          
        </el-row>
        <!-- 16. 6分钟步行测试 -->
        <el-row>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="16. 6分钟步行测试" class="item">
                <el-select
                  v-model="formJcjg.jcjg['6分钟步行测试']['是否检测过']"
                  placeholder="请选择是否检测"
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
              <el-form-item label="步行距离" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['6分钟步行测试']['步行测试内容']['步行距离']
                  "
                  placeholder="步行距离"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="步行前心率" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['6分钟步行测试']['步行测试内容']['步行前心率']
                  "
                  placeholder="步行前心率"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="步行最快心率" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['6分钟步行测试']['步行测试内容'][
                      '步行最快心率'
                    ]
                  "
                  placeholder="步行最快心率"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>

          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="心率变化绝对值" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['6分钟步行测试']['步行测试内容'][
                      '心率变化绝对值'
                    ]
                  "
                  placeholder="心率变化绝对值"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>

          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="心率变异分数" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['6分钟步行测试']['步行测试内容'][
                      '心率变异分数'
                    ]
                  "
                  placeholder="心率变异分数"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="步行前血压" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['6分钟步行测试']['步行测试内容']['步行前血压']
                  "
                  placeholder="步行前血压"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="步行最高血压" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['6分钟步行测试']['步行测试内容'][
                      '步行最高血压'
                    ]
                  "
                  placeholder="步行最高血压"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="血压变化绝对值" class="item">
                <el-input
                  v-model="
                    formJcjg.jcjg['6分钟步行测试']['步行测试内容'][
                      '血压变化绝对值'
                    ]
                  "
                  placeholder="血压变化绝对值"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="因骨关节等病活动困难" class="item">
                <el-select
                  v-model="
                    formJcjg.jcjg['6分钟步行测试']['步行测试内容'][
                      '因骨关节等病活动困难'
                    ]
                  "
                  placeholder="请选择是否因骨关节等病活动困难"
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
              <el-form-item label="其它影响步行实验" class="item">
                <el-select
                  v-model="
                    formJcjg.jcjg['6分钟步行测试']['步行测试内容'][
                      '其它影响步行实验'
                    ]
                  "
                  placeholder="请选择其它影响步行实验"
                >
                  <el-option
                    v-for="item in qtyxbxsy"
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
        <el-button type="primary" @click="submitForm('formJcjg')"
          >保存</el-button
        >
        <el-button @click="resetForm()">重置</el-button>

      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "Recordjcjg",
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
       // 心电图节律
      xdtjl: ["窦性心律", "心房颤动/心房扑动", "起搏心律", "室性早搏"],
      //其它影响步行实验
      qtyxbxsy: ["慢性肺部疾患", "贫血", "恶病质", "其他"],
      formJcjg: {
        record_id: "",
        name: "",
        jcjg: {
          "空腹血糖(mmol/l)": "",
          "HbA1c(%)": "",
          "血清肌酐(mmol/l)": "",
          "血红蛋白(mmol/l)": "",
          "钠(mmol/l)": "",
          "钾(mmol/l)": "",
          "总胆固醇(mmol/l)": "",
          "低密度脂蛋白(mmol/l)": "",
          "尿酸(mmol/l)": "",
          "BNP(pg/ml)": "",
          "NT-proBNP(pg/ml)": "",
          "同型半胱氨酸(mmol/l)": "",
          C反应蛋白: "",
          "铁蛋白(血清蛋白mg/l)": "",
          心电图: {
            是否检测过: "",
            心电图内容: {
              心电图日期: "",
              "心率(次/分)": "",
              心电图节律: "",
              左束支传导阻滞: "",
              "QRS时限(ms)": "",
            },
          },
          "超声心动图(近12月内)": {
            是否检测过: "",
            超声心动图内容: {
              日期: "",
              "射血分数(%)": "",
              "左心室舒张末期内径(mm)": "",
              "左心房舒张末期内径(mm)": "",
              "E/A": "",
              "E/e": "",
              肺静脉血流图: "",
            },
          },
          "6分钟步行测试": {
            是否检测过: "",
            步行测试内容: {
              步行距离: "",
              步行前心率: "",
              步行最快心率: "",
              心率变化绝对值: "",
              心率变异分数: "",
              步行前血压: "",
              步行最高血压: "",
              血压变化绝对值: "",
              因骨关节等病活动困难: "",
              其它影响步行实验: "",
            },
          },
        },
      },
    };
  },
  methods: {
    resetForm() {
      this.formJcjg.jcjg["空腹血糖(mmol/l)"] = null;
      this.formJcjg.jcjg["HbA1c(%)"] = null;
      this.formJcjg.jcjg["血清肌酐(mmol/l)"] = null;
      this.formJcjg.jcjg["血红蛋白(mmol/l)"] = null;
      this.formJcjg.jcjg["钠(mmol/l)"] = null;
      this.formJcjg.jcjg["钾(mmol/l)"] = null;
      this.formJcjg.jcjg["总胆固醇(mmol/l)"] = null;
      this.formJcjg.jcjg["低密度脂蛋白(mmol/l)"] = null;
      this.formJcjg.jcjg["尿酸(mmol/l)"] = null;
      this.formJcjg.jcjg["BNP(pg/ml)"] = null;
      this.formJcjg.jcjg["NT-proBNP(pg/ml)"] = null;
      this.formJcjg.jcjg["同型半胱氨酸(mmol/l)"] = null;
      this.formJcjg.jcjg["C反应蛋白"] = null;
      this.formJcjg.jcjg["铁蛋白(血清蛋白mg/l)"] = null;
      this.formJcjg.jcjg["心电图"]["心电图是否检测"] = null;
      this.formJcjg.jcjg["心电图"]["心电图日期"] = null;
      this.formJcjg.jcjg["心电图"]["心率(次/分)"] = null;
      this.formJcjg.jcjg["心电图"]["心电图节律"] = null;
      this.formJcjg.jcjg["心电图"]["左束支传导阻滞"] = null;
      this.formJcjg.jcjg["心电图"]["QRS时限(ms)"] = null;
      this.formJcjg.jcjg["超声心动图(近12月内)"]["是否检测过"] = null;
      this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["日期"] = null;
      this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["射血分数(%)"] = null;
      this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["左心室舒张末期内径(mm)"] = null;
      this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["左心房舒张末期内径(mm)"] = null;
      this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["E/A"] = null;
      this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["E/e"] = null;
      this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["肺静脉血流图"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["是否检测过"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["步行距离"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["步行前心率"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["步行最快心率"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["心率变化绝对值"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["心率变异分数"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["步行前血压"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["步行最高血压"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["血压变化绝对值"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["因骨关节等病活动困难"] = null;
      this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["其它影响步行实验"] = null;
    },
    initFormJcjg() {},
    loadJcjgData() {
      console.log("------loadjcjgData-------");
      this.resetForm();
      let record_id = this.record_id;
      // 读取数据
      this.getRequest("/visit/record/" + record_id).then((resp) => {
        if (resp.jcjg) {
          this.formJcjg.jcjg["空腹血糖(mmol/l)"] = JSON.parse(resp.jcjg)["空腹血糖(mmol/l)"];
          this.formJcjg.jcjg["HbA1c(%)"] = JSON.parse(resp.jcjg)["HbA1c(%)"];
          this.formJcjg.jcjg["血清肌酐(mmol/l)"] = JSON.parse(resp.jcjg)["血清肌酐(mmol/l)"];
          this.formJcjg.jcjg["血红蛋白(mmol/l)"] = JSON.parse(resp.jcjg)[ "血红蛋白(mmol/l)"];
          this.formJcjg.jcjg["钠(mmol/l)"] = JSON.parse(resp.jcjg)["钠(mmol/l)"];
          this.formJcjg.jcjg["钾(mmol/l)"] = JSON.parse(resp.jcjg)[
            "钾(mmol/l)"
          ];
          this.formJcjg.jcjg["总胆固醇(mmol/l)"] = JSON.parse(resp.jcjg)["总胆固醇(mmol/l)"];
          this.formJcjg.jcjg["低密度脂蛋白(mmol/l)"] = JSON.parse(resp.jcjg)["低密度脂蛋白(mmol/l)"];
          this.formJcjg.jcjg["尿酸(mmol/l)"] = JSON.parse(resp.jcjg)[
            "尿酸(mmol/l)"
          ];
          this.formJcjg.jcjg["BNP(pg/ml)"] = JSON.parse(resp.jcjg)["BNP(pg/ml)"];
          this.formJcjg.jcjg["NT-proBNP(pg/ml)"] = JSON.parse(resp.jcjg)[
            "NT-proBNP(pg/ml)"
          ];
          this.formJcjg.jcjg["同型半胱氨酸(mmol/l)"] = JSON.parse(resp.jcjg)[
            "同型半胱氨酸(mmol/l)"
          ];
          this.formJcjg.jcjg["C反应蛋白"] = JSON.parse(resp.jcjg)["C反应蛋白"];
          this.formJcjg.jcjg["铁蛋白(血清蛋白mg/l)"] = JSON.parse(resp.jcjg)["铁蛋白(血清蛋白mg/l)"];
          this.formJcjg.jcjg["心电图"]["心电图是否检测"] = JSON.parse(resp.jcjg)["心电图"]["心电图是否检测"];
          this.formJcjg.jcjg["心电图"]["心电图日期"] = JSON.parse(resp.jcjg)["心电图"]["心电图日期"];
          this.formJcjg.jcjg["心电图"]["心率(次/分)"] = JSON.parse(resp.jcjg)["心电图"]["心率(次/分)"];
          this.formJcjg.jcjg["心电图"]["心电图节律"] = JSON.parse(resp.jcjg)["心电图"]["心电图节律"];
          this.formJcjg.jcjg["心电图"]["左束支传导阻滞"] = JSON.parse(resp.jcjg)["心电图"]["左束支传导阻滞"];
          this.formJcjg.jcjg["心电图"]["QRS时限(ms)"] = JSON.parse(resp.jcjg)["心电图"]["QRS时限(ms)"];
          this.formJcjg.jcjg["超声心动图(近12月内)"]["是否检测过"] = JSON.parse(resp.jcjg)["超声心动图(近12月内)"]["是否检测过"];
          this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["日期"] = JSON.parse(resp.jcjg)["超声心动图(近12月内)"]["超声心动图内容"]["日期"];
          this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["射血分数(%)"] = JSON.parse(resp.jcjg)["超声心动图(近12月内)"]["超声心动图内容"]["射血分数(%)"];
          this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["左心室舒张末期内径(mm)"] = JSON.parse(resp.jcjg)["超声心动图(近12月内)"]["超声心动图内容"]["左心室舒张末期内径(mm)"];
          this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["肺静脉血流图"] = JSON.parse(resp.jcjg)["超声心动图(近12月内)"]["超声心动图内容"]["肺静脉血流图"];
          this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["E/A"] = JSON.parse(resp.jcjg)["超声心动图(近12月内)"]["超声心动图内容"]["E/A"];
          this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["E/e"] = JSON.parse(resp.jcjg)["超声心动图(近12月内)"]["超声心动图内容"]["E/e"];
          this.formJcjg.jcjg["超声心动图(近12月内)"]["超声心动图内容"]["左心房舒张末期内径(mm)"] = JSON.parse(resp.jcjg)["超声心动图(近12月内)"]["超声心动图内容"]["左心房舒张末期内径(mm)"];
          this.formJcjg.jcjg["6分钟步行测试"]["是否检测过"] = JSON.parse(resp.jcjg)["6分钟步行测试"]["是否检测过"];
          this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["步行距离"] = JSON.parse(resp.jcjg)["6分钟步行测试"]["步行测试内容"]["步行距离"];
          this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["步行前心率"]  = JSON.parse(resp.jcjg)["6分钟步行测试"]["步行测试内容"]["步行前心率"] ;
          this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["步行最快心率"] = JSON.parse(resp.jcjg)["6分钟步行测试"]["步行测试内容"]["步行最快心率"];
          this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["心率变化绝对值"] = JSON.parse(resp.jcjg)["6分钟步行测试"]["步行测试内容"]["心率变化绝对值"];
          this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["心率变异分数"] = JSON.parse(resp.jcjg)["6分钟步行测试"]["步行测试内容"]["心率变异分数"];
          this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["步行前血压"] = JSON.parse(resp.jcjg)["6分钟步行测试"]["步行测试内容"]["步行前血压"];
          this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["步行最高血压"] = JSON.parse(resp.jcjg)["6分钟步行测试"]["步行测试内容"]["步行最高血压"];
          this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["血压变化绝对值"] = JSON.parse(resp.jcjg)["6分钟步行测试"]["步行测试内容"]["血压变化绝对值"];
          this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["因骨关节等病活动困难"] = JSON.parse(resp.jcjg)["6分钟步行测试"]["步行测试内容"]["因骨关节等病活动困难"];
          this.formJcjg.jcjg["6分钟步行测试"]["步行测试内容"]["其它影响步行实验"] = JSON.parse(resp.jcjg)["6分钟步行测试"]["步行测试内容"]["其它影响步行实验"];
        }
      });
    },
    submitForm() {
      this.formJcjg.record_id = this.record_id;
      var formData = JSON.stringify(this.formJcjg);
      console.log("this.formJcjg", this.formJcjg);
      this.putRequest("/visit/record/jcjg/", this.formJcjg).then((resp) => {
        if (resp) {
          this.loadJcjgData();
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
    this.loadJcjgData();
  },
  watch: {
    record_id: function (newData, oldData) {},
  },
};
</script>