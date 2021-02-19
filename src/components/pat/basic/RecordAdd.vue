<template>
  <el-form
    ref="formAdd"
    :model="formAdd"
    :rules="rules"
    label-width="180px"
    label-position="left"
    :inline="true"
  >
    <el-tabs v-model="activeAdd" type="card">
      <!-- 随访基本信息 -->
      <el-tab-pane label="随访基本信息" name="add_first">
        <el-row>
          <!-- 随访类型 -->
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="随访类型" prop="record_type">
                <el-select v-model="formAdd.record_type" placeholder="随访类型">
                  <el-option
                    v-for="item in sflxList"
                    :key="item.key"
                    :value="item.key"
                    :label="item.value"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
        </el-row>
        <el-row>
          <!-- 随访日期 -->
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="随访日期" class="item" prop="vist_time">
                <el-date-picker
                  v-model="formAdd.vist_time"
                  type="date"
                  placeholder="选择日期"
                ></el-date-picker>
              </el-form-item>
            </div>
          </el-col>
          <!-- 随访形式 -->
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="随访形式" class="item" prop="sfxs">
                <el-select v-model="formAdd.sfxs" placeholder="随访形式">
                  <el-option
                    v-for="item in sfxsList"
                    :key="item.key"
                    :value="item.key"
                    :label="item.value"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
        </el-row>
      </el-tab-pane>

      <!-- 随访症状 -->
      <el-tab-pane label="随访症状" name="add_second">
        <div>
          <!-- 患者症状 -->
          <el-row>
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="1.乏力与疲劳" class="item">
                  <el-select
                    v-model="formAdd.hzzz['乏力与疲劳']"
                    placeholder="请选择乏力与疲劳"
                    clearable
                  >
                    <el-option
                      v-for="item in template_data.症状.乏力与疲劳"
                      :key="item"
                      :value="item"
                    ></el-option>
                  </el-select>
                </el-form-item>
              </div>
            </el-col>

            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="2.气短/呼吸困难" class="item">
                  <el-select
                    v-model="formAdd.hzzz['气短/呼吸困难']"
                    placeholder="请选择气短/呼吸困难"
                  >
                    <el-option
                      v-for="item in template_data.症状['气短/呼吸困难']"
                      :key="item"
                      :value="item"
                    ></el-option>
                  </el-select>
                </el-form-item>
              </div>
            </el-col>
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="3.活动能力" class="item">
                  <el-select
                    v-model="formAdd.hzzz['活动能力']"
                    placeholder="请选择活动能力"
                  >
                    <el-option
                      v-for="item in template_data.症状.活动能力"
                      :key="item"
                      :value="item"
                    ></el-option>
                  </el-select>
                </el-form-item>
              </div>
            </el-col>
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="4.自理能力" class="item">
                  <el-select
                    v-model="formAdd.hzzz['自理能力']"
                    placeholder="请选择自理能力"
                  >
                    <el-option
                      v-for="item in template_data.症状.自理能力"
                      :key="item"
                      :value="item"
                    ></el-option>
                  </el-select>
                </el-form-item>
              </div>
            </el-col>
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="5.日常活动" class="item">
                  <el-select
                    v-model="formAdd.hzzz['日常活动']"
                    placeholder="请选择日常活动"
                  >
                    <el-option
                      v-for="item in template_data.症状.日常活动"
                      :key="item"
                      :value="item"
                    ></el-option>
                  </el-select>
                </el-form-item>
              </div>
            </el-col>
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="6.其它躯体不适" class="item">
                  <el-select
                    v-model="formAdd.hzzz['其它躯体不适']"
                    placeholder="请选择其它躯体不适"
                  >
                    <el-option
                      v-for="item in template_data.症状.其它躯体不适"
                      :key="item"
                      :value="item"
                    ></el-option>
                  </el-select>
                </el-form-item>
              </div>
            </el-col>
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="7.焦虑/抑郁" class="item">
                  <el-select
                    v-model="formAdd.hzzz['焦虑/抑郁']"
                    placeholder="请选择焦虑/抑郁"
                  >
                    <el-option
                      v-for="item in template_data.症状['焦虑/抑郁']"
                      :key="item"
                      :value="item"
                    ></el-option>
                  </el-select>
                </el-form-item>
              </div>
            </el-col>
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="8.生活质量自评(分)" class="item">
                  <el-input
                    v-model="formAdd.hzzz['生活质量自评']"
                    placeholder="请输入生活质量自评"
                    maxlength="4"
                  ></el-input>
                </el-form-item>
                <!-- 备注：0-100分，100分最高 -->
              </div>
            </el-col>
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="9.充血性心力衰竭症状" class="item">
                  <el-select
                    v-model="formAdd.hzzz['充血性心力衰竭症状']"
                    placeholder="请选择充血性心力衰竭症状"
                  >
                    <el-option
                      v-for="item in template_data.症状['充血性心力衰竭症状']"
                      :key="item"
                      :value="item"
                    ></el-option>
                  </el-select>
                </el-form-item>
              </div>
            </el-col>
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="心脏协会分级" class="item">
                  <el-select
                    v-model="formAdd.hzzz['心力衰竭症状等级']"
                    placeholder="请选择心力衰竭症状等级"
                  >
                    <el-option
                      v-for="item in template_data.症状['心力衰竭症状等级']"
                      :key="item"
                      :value="item"
                    ></el-option>
                  </el-select>
                </el-form-item>
              </div>
            </el-col>
          </el-row>
          <el-tag style="margin-right: 5px; margin-bottom: 10px" type="danger"
            >* 8. 生活质量自评0-100分，0为生活质量最低，100为最高！</el-tag
          >
        </div>
      </el-tab-pane>

      <el-tab-pane label="生活方式" name="add_third">
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="1.饮酒情况" class="item">
              <!-- <el-select v-model="formAdd.shfs['饮酒情况']" placeholder="请选择饮酒情况">
                <el-option v-for="item in template_data.生活方式['饮酒情况']" :key="item" :value="item"></el-option>
              </el-select>-->
              <el-autocomplete
                popper-class="my-autocomplete"
                v-model="formAdd.shfs['饮酒情况']"
                :fetch-suggestions="queryYjSearch"
                placeholder="请输入饮酒情况"
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
            <el-form-item label="2.吸烟情况" class="item">
              <!-- 
              <el-select v-model="formAdd.shfs['吸烟情况']" placeholder="请选择吸烟情况">
                <el-option v-for="item in template_data.生活方式['吸烟情况']" :key="item" :value="item"></el-option>
              </el-select>-->

              <el-autocomplete
                popper-class="my-autocomplete"
                v-model="formAdd.shfs['吸烟情况']"
                :fetch-suggestions="queryXySearch"
                placeholder="请输入吸烟情况"
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
            <el-form-item label="3.基础血压低" class="item">
              <el-select
                v-model="formAdd.shfs['基础血压低']"
                placeholder="请选择基础血压低"
              >
                <el-option
                  v-for="item in template_data.生活方式['基础血压低']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="4.基础心率低" class="item">
              <el-select
                v-model="formAdd.shfs['基础心率低']"
                placeholder="请选择基础心率低"
              >
                <el-option
                  v-for="item in template_data.生活方式['基础心率低']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="5.治疗依从性高" class="item">
              <el-select
                v-model="formAdd.shfs['治疗依从性高']"
                placeholder="请选择治疗依从性高"
              >
                <el-option
                  v-for="item in template_data.生活方式['治疗依从性高']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="7.患者本人重视程度高" class="item">
              <el-select
                v-model="formAdd.shfs['患者本人重视程度高']"
                placeholder="请选择患者本人重视程度高"
              >
                <el-option
                  v-for="item in template_data.生活方式['患者本人重视程度高']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="9.患者本人信心" class="item">
              <el-select
                v-model="formAdd.shfs['患者本人信心']"
                placeholder="请选择患者本人信心"
              >
                <el-option
                  v-for="item in template_data.生活方式['患者本人信心']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="10.家属关心程度" class="item">
              <el-select
                v-model="formAdd.shfs['家属关心程度']"
                placeholder="请选择家属关心程度"
              >
                <el-option
                  v-for="item in template_data.生活方式['家属关心程度']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="11.有氧运动" class="item">
              <el-select
                v-model="formAdd.shfs['有氧运动']"
                placeholder="请选择有氧运动"
              >
                <el-option
                  v-for="item in template_data.生活方式['有氧运动']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="13.经济条件(生活及治病)" class="item">
              <el-select
                v-model="formAdd.shfs['经济条件']"
                placeholder="经济条件(满足生活及治病需要)"
              >
                <el-option
                  v-for="item in template_data.生活方式['经济条件']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="14.对社会及生活的情感" class="item">
              <el-select
                v-model="formAdd.shfs['对社会及生活的情感']"
                placeholder="请选择对社会及生活的情感"
              >
                <el-option
                  v-for="item in template_data.生活方式['对社会及生活的情感']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="15.人际关系" class="item">
              <el-select
                v-model="formAdd.shfs['人际关系']"
                placeholder="请选择人际关系"
              >
                <el-option
                  v-for="item in template_data.生活方式['人际关系']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="16.对患病及衰老的态度" class="item">
              <el-select
                v-model="formAdd.shfs['对患病及衰老的态度']"
                placeholder="请选择对患病及衰老的态度"
              >
                <el-option
                  v-for="item in template_data.生活方式['对患病及衰老的态度']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="17.每天进食食盐" class="item">
              <el-select
                v-model="formAdd.shfs['每天进食食盐']"
                placeholder="请选择每天进食食盐"
              >
                <el-option
                  v-for="item in template_data.生活方式['每天进食食盐']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="18.食欲" class="item">
              <el-select
                v-model="formAdd.shfs['食欲']"
                placeholder="请选择食欲"
              >
                <el-option
                  v-for="item in template_data.生活方式['食欲']"
                  :key="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-form-item>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="19.平均每日入水量(ml)" class="item">
              <el-input
                v-model="formAdd.shfs['平均每日入水量(ml)']"
                placeholder="平均每日入水量(ml)"
                maxlength="4"
              ></el-input>
            </el-form-item>
          </div>
        </el-col>
      </el-tab-pane>

      <!-- 体格检查与生命体征 -->
      <el-tab-pane label="体格检查与生命体征" name="add_four">
        <el-row>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="1.体重(kg)" class="item">
                <el-input
                  v-model="formAdd.tzytg['体重(kg)']"
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
                  v-model="formAdd.tzytg['体重变化']"
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
                  v-model="formAdd.tzytg['体重指数']"
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
                  v-model="formAdd.tzytg['坐位动脉血压']"
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
                  v-model="formAdd.tzytg['静息心率(次/分)']"
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
                  v-model="formAdd.tzytg['外周血氧饱和度(%)']"
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
                  v-model="formAdd.tzytg['肺咯音']"
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
                  v-model="formAdd.tzytg['颈静脉压升高体征']"
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
                  v-model="formAdd.tzytg['外周性水肿']"
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
                  v-model="formAdd.tzytg['第三心音']"
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
                  v-model="formAdd.tzytg['外周滴灌注体征']"
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
                  v-model="formAdd.tzytg['肝颈静脉回流征']"
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
                  v-model="formAdd.tzytg['皮肤湿度']"
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
      </el-tab-pane>

      <el-tab-pane label="检测结果（电话随访可不填）" name="add_five">
        <el-row>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="1.空腹血糖(mmol/l)" class="item">
                <el-input
                  v-model="formAdd.jcjg['空腹血糖(mmol/l)']"
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
                  v-model="formAdd.jcjg['HbA1c(%)']"
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
                  v-model="formAdd.jcjg['血清肌酐(mmol/l)']"
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
                  v-model="formAdd.jcjg['血红蛋白(mmol/l)']"
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
                  v-model="formAdd.jcjg['钠(mmol/l)']"
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
                  v-model="formAdd.jcjg['钾(mmol/l)']"
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
                  v-model="formAdd.jcjg['总胆固醇(mmol/l)']"
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
                  v-model="formAdd.jcjg['低密度脂蛋白(mmol/l)']"
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
                  v-model="formAdd.jcjg['尿酸(mmol/l)']"
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
                  v-model="formAdd.jcjg['BNP(pg/ml)']"
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
                  v-model="formAdd.jcjg['NT-proBNP(pg/ml)']"
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
                  v-model="formAdd.jcjg['同型半胱氨酸(mmol/l)']"
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
                  v-model="formAdd.jcjg['C反应蛋白']"
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
                  v-model="formAdd.jcjg['铁蛋白(血清蛋白mg/l)']"
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
                  v-model="formAdd.jcjg['心电图']['是否检测过']"
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
                  v-model="formAdd.jcjg['心电图']['心电图内容']['心电图日期']"
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
                  v-model="formAdd.jcjg['心电图']['心电图内容']['心率(次/分)']"
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
                  v-model="formAdd.jcjg['心电图']['心电图内容']['心电图节律']"
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
                    formAdd.jcjg['心电图']['心电图内容']['左束支传导阻滞']
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
                  v-model="formAdd.jcjg['心电图']['心电图内容']['QRS时限(ms)']"
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
                  v-model="formAdd.jcjg['超声心动图(近12月内)']['是否检测过']"
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
              <el-form-item label="超声心动图内容" class="item" prop="日期">
                <el-date-picker
                  v-model="
                    formAdd.jcjg['超声心动图(近12月内)']['超声心动图内容'][
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
                    formAdd.jcjg['超声心动图(近12月内)']['超声心动图内容'][
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
                    formAdd.jcjg['超声心动图(近12月内)']['超声心动图内容'][
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
              <el-form-item label="肺静脉血流图" class="item">
                <el-input
                  v-model="
                    formAdd.jcjg['超声心动图(近12月内)']['超声心动图内容'][
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
                    formAdd.jcjg['超声心动图(近12月内)']['超声心动图内容'][
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
                    formAdd.jcjg['超声心动图(近12月内)']['超声心动图内容'][
                      'E/e'
                    ]
                  "
                  placeholder="E/e"
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
                    formAdd.jcjg['超声心动图(近12月内)']['超声心动图内容'][
                      '左心房舒张末期内径(mm)'
                    ]
                  "
                  placeholder="左心房舒张末期内径(mm)"
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
                  v-model="formAdd.jcjg['6分钟步行测试']['是否检测过']"
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
                    formAdd.jcjg['6分钟步行测试']['步行测试内容']['步行距离']
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
                    formAdd.jcjg['6分钟步行测试']['步行测试内容']['步行前心率']
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
                    formAdd.jcjg['6分钟步行测试']['步行测试内容'][
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
                    formAdd.jcjg['6分钟步行测试']['步行测试内容'][
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
                    formAdd.jcjg['6分钟步行测试']['步行测试内容'][
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
                    formAdd.jcjg['6分钟步行测试']['步行测试内容']['步行前血压']
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
                    formAdd.jcjg['6分钟步行测试']['步行测试内容'][
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
                    formAdd.jcjg['6分钟步行测试']['步行测试内容'][
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
                    formAdd.jcjg['6分钟步行测试']['步行测试内容'][
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
                    formAdd.jcjg['6分钟步行测试']['步行测试内容'][
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
      </el-tab-pane>

      <el-tab-pane label="治疗药物A(心血管药物)" name="add_six">
        <!-- 血管紧张素转化为酶抑制剂（ACEI） -->
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>1. 血管紧张素转化为酶抑制剂（ACEI）</span>
          </div>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="是否使用" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ACEI['是否使用']"
                  placeholder="请选择是否使用"
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
              <el-form-item label="未用原因" class="item">
                <el-autocomplete
                  popper-class="my-autocomplete"
                  v-model="formAdd.zlyw_a.ACEI['未用']['原因']"
                  :fetch-suggestions="queryReasonASearch"
                  placeholder="请输入未用原因"
                  @select="handleSelect"
                >
                  <i
                    class="el-icon-edit el-input__icon"
                    slot="suffix"
                    @click="handleIconClick"
                  ></i>
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
              <el-form-item label="症状" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ACEI['未用']['症状']"
                  placeholder="请选择症状"
                  multiple
                  filterable
                  allow-create
                >
                  <el-option
                    v-for="item in reason_b"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>

          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物名称" class="item">
                <el-autocomplete
                  popper-class="my-autocomplete"
                  v-model="formAdd.zlyw_a.ACEI['已用']['药物名称']"
                  :fetch-suggestions="queryACEIywmcSearch"
                  placeholder="请输入药物名称"
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
              <el-form-item label="药品剂量(mg/d)" class="item">
                <el-input
                  v-model="formAdd.zlyw_a.ACEI['已用']['药物剂量(mg/d)']"
                  placeholder="请输入药物剂量"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物达到目标剂量" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ACEI['已用']['是否达到目标剂量']"
                  placeholder="请选择是否达到目标剂量"
                >
                  <el-option
                    v-for="item in this.base_selarr"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="未达目标剂量理由" class="item">
                <el-input
                  v-model="formAdd.zlyw_a.ACEI['已用']['未达目标剂量理由']"
                  placeholder="请输入未达到目标剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物是否增加剂量" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ACEI['已用']['是否增加剂量']"
                  placeholder="请选择是否增加剂量"
                >
                  <el-option
                    v-for="item in this.base_selarr"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="未增剂量理由" class="item">
                <el-input
                  v-model="formAdd.zlyw_a.ACEI['已用']['未增剂量理由']"
                  placeholder="请输入未增剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
        </el-card>

        <!-- ARNI -->
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>2. 血管紧张素受体脑啡肽酶抑制剂（ARNI）</span>
            <!-- <el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button> -->
          </div>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="是否使用" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ARNI['是否使用']"
                  placeholder="请选择是否使用"
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
              <el-form-item label="药物名称" class="item">
                <el-autocomplete
                  popper-class="my-autocomplete"
                  v-model="formAdd.zlyw_a.ARNI['已用']['药物名称']"
                  :fetch-suggestions="queryARNIywmcSearch"
                  placeholder="请输入药物名称"
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
              <el-form-item label="药品剂量(mg/d)" class="item">
                <el-input
                  v-model="formAdd.zlyw_a.ARNI['已用']['药物剂量(mg/d)']"
                  placeholder="请输入药物剂量"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物达到目标剂量" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ARNI['已用']['是否达到目标剂量']"
                  placeholder="请选择是否达到目标剂量"
                >
                  <el-option
                    v-for="item in this.base_selarr"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="未达目标剂量理由" class="item">
                <el-input
                  v-model="formAdd.zlyw_a.ARNI['已用']['未达目标剂量理由']"
                  placeholder="请输入未达到目标剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物是否增加剂量" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ARNI['已用']['是否增加剂量']"
                  placeholder="请选择是否增加剂量"
                >
                  <el-option
                    v-for="item in this.base_selarr"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="未增剂量理由" class="item">
                <el-input
                  v-model="formAdd.zlyw_a.ARNI['已用']['未增剂量理由']"
                  placeholder="请输入未增剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
        </el-card>

        <!-- 3. 血管紧张素受体抑制剂（ARB） -->
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>3. 血管紧张素受体抑制剂（ARB）</span>
          </div>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="是否使用" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ARB['是否使用']"
                  placeholder="请选择是否使用"
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
              <el-form-item label="未用原因" class="item">
                <el-autocomplete
                  popper-class="my-autocomplete"
                  v-model="formAdd.zlyw_a.ARB['未用']['原因']"
                  :fetch-suggestions="queryReasonASearch"
                  placeholder="请输入未用原因"
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
              <el-form-item label="症状" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ARB['未用']['症状']"
                  placeholder="请选择症状"
                  multiple
                  filterable
                  allow-create
                >
                  <el-option
                    v-for="item in reason_b"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>

          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物名称" class="item">
                <el-autocomplete
                  popper-class="my-autocomplete"
                  v-model="formAdd.zlyw_a.ARB['已用']['药物名称']"
                  :fetch-suggestions="queryACEIywmcSearch"
                  placeholder="请输入药物名称"
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
              <el-form-item label="药品剂量(mg/d)" class="item">
                <el-input
                  v-model="formAdd.zlyw_a.ARB['已用']['药物剂量(mg/d)']"
                  placeholder="请输入药物剂量"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物达到目标剂量" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ARB['已用']['是否达到目标剂量']"
                  placeholder="请选择是否达到目标剂量"
                >
                  <el-option
                    v-for="item in this.base_selarr"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="未达目标剂量理由" class="item">
                <el-input
                  v-model="formAdd.zlyw_a.ARB['已用']['未达目标剂量理由']"
                  placeholder="请输入未达到目标剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物是否增加剂量" class="item">
                <el-select
                  v-model="formAdd.zlyw_a.ARB['已用']['是否增加剂量']"
                  placeholder="请选择是否增加剂量"
                >
                  <el-option
                    v-for="item in this.base_selarr"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="未增剂量理由" class="item">
                <el-input
                  v-model="formAdd.zlyw_a.ARB['已用']['未增剂量理由']"
                  placeholder="请输入未增剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
        </el-card>

        <!-- 4. β受体阻滞剂 -->
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>4. β-受体阻滞剂</span>
            <!-- <el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button> -->
          </div>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="是否使用" class="item">
                <el-select
                  v-model="formAdd.zlyw_a['β受体阻滞剂']['是否使用']"
                  placeholder="请选择是否使用"
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
              <el-form-item label="药物名称" class="item">
                <el-autocomplete
                  popper-class="my-autocomplete"
                  v-model="formAdd.zlyw_a['β受体阻滞剂']['已用']['药物名称']"
                  :fetch-suggestions="queryARNIywmcSearch"
                  placeholder="请输入药物名称"
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
              <el-form-item label="药品剂量(mg/d)" class="item">
                <el-input
                  v-model="
                    formAdd.zlyw_a['β受体阻滞剂']['已用']['药物剂量(mg/d)']
                  "
                  placeholder="请输入药物剂量"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物达到目标剂量" class="item">
                <el-select
                  v-model="
                    formAdd.zlyw_a['β受体阻滞剂']['已用']['是否达到目标剂量']
                  "
                  placeholder="请选择是否达到目标剂量"
                >
                  <el-option
                    v-for="item in this.base_selarr"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="未达目标剂量理由" class="item">
                <el-input
                  v-model="
                    formAdd.zlyw_a['β受体阻滞剂']['已用']['未达目标剂量理由']
                  "
                  placeholder="请输入未达到目标剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物是否增加剂量" class="item">
                <el-select
                  v-model="
                    formAdd.zlyw_a['β受体阻滞剂']['已用']['是否增加剂量']
                  "
                  placeholder="请选择是否增加剂量"
                >
                  <el-option
                    v-for="item in this.base_selarr"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="未增剂量理由" class="item">
                <el-input
                  v-model="
                    formAdd.zlyw_a['β受体阻滞剂']['已用']['未增剂量理由']
                  "
                  placeholder="请输入未增剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
        </el-card>

        <!-- 5. 醛固酮受体阻断剂 -->
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>5. 醛固酮受体阻断剂</span>
          </div>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="是否使用" class="item">
                <el-select
                  v-model="formAdd.zlyw_a['醛固酮受体阻断剂']['是否使用']"
                  placeholder="请选择是否使用"
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
              <el-form-item label="药物名称" class="item">
                <el-autocomplete
                  popper-class="my-autocomplete"
                  v-model="
                    formAdd.zlyw_a['醛固酮受体阻断剂']['已用']['药物名称']
                  "
                  :fetch-suggestions="queryARNIywmcSearch"
                  placeholder="请输入药物名称"
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
              <el-form-item label="药品剂量(mg/d)" class="item">
                <el-input
                  v-model="
                    formAdd.zlyw_a['醛固酮受体阻断剂']['已用']['药物剂量(mg/d)']
                  "
                  placeholder="请输入药物剂量"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="有无症状(NYHA分级为I)" class="item">
                <el-select
                  v-model="
                    formAdd.zlyw_a['醛固酮受体阻断剂']['有无症状(NYHA分级为I)']
                  "
                  placeholder="请选择有无症状(NYHA分级为I)"
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
        </el-card>

        <!-- 7. 伊伐布雷定 -->
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>7. 伊伐布雷定</span>
          </div>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="是否使用" class="item">
                <el-select
                  v-model="formAdd.zlyw_a['伊伐布雷定']['是否使用']"
                  placeholder="请选择是否使用"
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
              <el-form-item label="未用原因" class="item">
                <el-autocomplete
                  popper-class="my-autocomplete"
                  v-model="formAdd.zlyw_a['伊伐布雷定']['未用']['原因']"
                  :fetch-suggestions="queryReasonASearch"
                  placeholder="请输入未用原因"
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
              <el-form-item label="禁忌不耐受症状" class="item">
                <el-select
                  v-model="formAdd.zlyw_a['伊伐布雷定']['未用']['症状']"
                  placeholder="请选择症状"
                  multiple
                  filterable
                  allow-create
                >
                  <el-option
                    v-for="item in reason_b"
                    :key="item"
                    :value="item"
                  ></el-option>
                </el-select>
              </el-form-item>
            </div>
          </el-col>

          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物名称" class="item">
                <el-autocomplete
                  popper-class="my-autocomplete"
                  v-model="formAdd.zlyw_a['伊伐布雷定']['已用']['药物名称']"
                  :fetch-suggestions="queryACEIywmcSearch"
                  placeholder="请输入药物名称"
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
              <el-form-item label="药品剂量(mg/d)" class="item">
                <el-input
                  v-model="
                    formAdd.zlyw_a['伊伐布雷定']['已用']['药物剂量(mg/d)']
                  "
                  placeholder="请输入药物剂量"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
        </el-card>

        <el-collapse v-model="activeNames" >
          <!-- 8. 噻嗪类利尿剂 -->
          <el-collapse-item title="8. 噻嗪类利尿剂" name="sqlllj">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['噻嗪类利尿剂']['是否使用']"
                    placeholder="请选择是否使用"
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
                <el-form-item label="药物名称" class="item">
                  <el-autocomplete
                    popper-class="my-autocomplete"
                    v-model="formAdd.zlyw_a['噻嗪类利尿剂']['已用']['药物名称']"
                    :fetch-suggestions="queryARNIywmcSearch"
                    placeholder="请输入药物名称"
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
                <el-form-item label="药品剂量(mg/d)" class="item">
                  <el-input
                    v-model="
                      formAdd.zlyw_a['噻嗪类利尿剂']['已用']['药物剂量(mg/d)']
                    "
                    placeholder="请输入药物剂量"
                    maxlength="4"
                  ></el-input>
                </el-form-item>
              </div>
            </el-col>
          </el-collapse-item>

          <!-- 9. 髓袢利尿剂 -->
          <el-collapse-item title="9. 髓袢利尿剂" name="sbllj">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['髓袢利尿剂']['是否使用']"
                    placeholder="请选择是否使用"
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
                <el-form-item label="药物名称" class="item">
                  <el-autocomplete
                    popper-class="my-autocomplete"
                    v-model="formAdd.zlyw_a['髓袢利尿剂']['已用']['药物名称']"
                    :fetch-suggestions="queryARNIywmcSearch"
                    placeholder="请输入药物名称"
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
                <el-form-item label="药品剂量(mg/d)" class="item">
                  <el-input
                    v-model="
                      formAdd.zlyw_a['髓袢利尿剂']['已用']['药物剂量(mg/d)']
                    "
                    placeholder="请输入药物剂量"
                    maxlength="4"
                  ></el-input>
                </el-form-item>
              </div>
            </el-col>
          </el-collapse-item>

          <!-- 10. 地高辛 -->
          <el-collapse-item title="10. 地高辛" name="gdx">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['地高辛']['是否使用']"
                    placeholder="请选择是否使用"
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
                <el-form-item label="药品剂量(mg/d)" class="item">
                  <el-input
                    v-model="formAdd.zlyw_a['地高辛']['药物剂量(mg/d)']"
                    placeholder="请输入药物剂量"
                    maxlength="4"
                  ></el-input>
                </el-form-item>
              </div>
            </el-col>
          </el-collapse-item>

          <!-- 11. 芪苈强心胶囊 -->
          <el-collapse-item title="11. 芪苈强心胶囊" name="slqxjn">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['芪苈强心胶囊']['是否使用']"
                    placeholder="请选择是否使用"
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
          </el-collapse-item>

          <!-- 12. 胺碘酮 -->
          <el-collapse-item title="12. 胺碘酮" name="adt">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['胺碘酮']['是否使用']"
                    placeholder="请选择是否使用"
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
                <el-form-item label="药品剂量(mg/d)" class="item">
                  <el-input
                    v-model="formAdd.zlyw_a['胺碘酮']['药物剂量(mg/d)']"
                    placeholder="请输入药物剂量"
                    maxlength="4"
                  ></el-input>
                </el-form-item>
              </div>
            </el-col>
          </el-collapse-item>

          <!-- 13. 其他抗心律失常药物 -->
          <el-collapse-item title="13. 其他抗心律失常药物" name="qtkxlsc">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['其他抗心律失常药物']['是否使用']"
                    placeholder="请选择是否使用"
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
          </el-collapse-item>

          <!-- 14. 抗血小板药 -->
          <el-collapse-item title="14. 抗血小板药" name="kxxby">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['抗血小板药']['是否使用']"
                    placeholder="请选择是否使用"
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
                <el-form-item label="药物名称" class="item">
                  <el-autocomplete
                    popper-class="my-autocomplete"
                    v-model="formAdd.zlyw_a['抗血小板药']['已用']['药物名称']"
                    :fetch-suggestions="queryARNIywmcSearch"
                    placeholder="请输入药物名称"
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
                <el-form-item label="药品剂量(mg/d)" class="item">
                  <el-input
                    v-model="formAdd.zlyw_a['抗血小板药']['药物剂量(mg/d)']"
                    placeholder="请输入药物剂量"
                    maxlength="4"
                  ></el-input>
                </el-form-item>
              </div>
            </el-col>
          </el-collapse-item>

          <!-- 15. 抗凝药 -->
          <el-collapse-item title="15. 抗凝药" name="kly">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['抗凝药']['是否使用']"
                    placeholder="请选择是否使用"
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
                <el-form-item label="药物名称" class="item">
                  <el-autocomplete
                    popper-class="my-autocomplete"
                    v-model="formAdd.zlyw_a['抗凝药']['已用']['药物名称']"
                    :fetch-suggestions="queryARNIywmcSearch"
                    placeholder="请输入药物名称"
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
                <el-form-item label="药品剂量(mg/d)" class="item">
                  <el-input
                    v-model="formAdd.zlyw_a['抗凝药']['药物剂量(mg/d)']"
                    placeholder="请输入药物剂量"
                    maxlength="4"
                  ></el-input>
                </el-form-item>
              </div>
            </el-col>
          </el-collapse-item>

          <!-- 16. 他汀类药物 -->
          <el-collapse-item title="16. 他汀类药物" name="tlxyw">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['他汀类药物']['是否使用']"
                    placeholder="请选择是否使用"
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
                <el-form-item label="药物名称" class="item">
                  <el-autocomplete
                    popper-class="my-autocomplete"
                    v-model="formAdd.zlyw_a['他汀类药物']['已用']['药物名称']"
                    :fetch-suggestions="queryARNIywmcSearch"
                    placeholder="请输入药物名称"
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
                <el-form-item label="药品剂量(mg/d)" class="item">
                  <el-input
                    v-model="formAdd.zlyw_a['他汀类药物']['药物剂量(mg/d)']"
                    placeholder="请输入药物剂量"
                    maxlength="4"
                  ></el-input>
                </el-form-item>
              </div>
            </el-col>
          </el-collapse-item>

          <!-- 17. 二氢吡啶类钙拮抗剂 -->
          <el-collapse-item title="17. 二氢吡啶类钙拮抗剂" name="eqpdl">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['二氢吡啶类钙拮抗剂']['是否使用']"
                    placeholder="请选择是否使用"
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
                <el-form-item label="药物名称" class="item">
                  <el-autocomplete
                    popper-class="my-autocomplete"
                    v-model="
                      formAdd.zlyw_a['二氢吡啶类钙拮抗剂']['已用']['药物名称']
                    "
                    :fetch-suggestions="queryARNIywmcSearch"
                    placeholder="请输入药物名称"
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
                <el-form-item label="药品剂量(mg/d)" class="item">
                  <el-input
                    v-model="
                      formAdd.zlyw_a['二氢吡啶类钙拮抗剂']['药物剂量(mg/d)']
                    "
                    placeholder="请输入药物剂量"
                    maxlength="4"
                  ></el-input>
                </el-form-item>
              </div>
            </el-col>
          </el-collapse-item>

          <!-- 18. 非二氢吡啶类钙拮抗剂 -->
          <el-collapse-item title="18. 非二氢吡啶类钙拮抗剂" name="feqpdlg">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['非二氢吡啶类钙拮抗剂']['是否使用']"
                    placeholder="请选择是否使用"
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
          </el-collapse-item>

          <!-- 19. 硝酸酯类药物 -->
          <el-collapse-item title="19. 硝酸酯类药物" name="xszlyw">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['硝酸酯类药物']['是否使用']"
                    placeholder="请选择是否使用"
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
                <el-form-item label="药物名称" class="item">
                  <el-autocomplete
                    popper-class="my-autocomplete"
                    v-model="formAdd.zlyw_a['硝酸酯类药物']['已用']['药物名称']"
                    :fetch-suggestions="queryARNIywmcSearch"
                    placeholder="请输入药物名称"
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
                <el-form-item label="药品剂量(mg/d)" class="item">
                  <el-input
                    v-model="formAdd.zlyw_a['硝酸酯类药物']['药物剂量(mg/d)']"
                    placeholder="请输入药物剂量"
                    maxlength="4"
                  ></el-input>
                </el-form-item>
              </div>
            </el-col>
          </el-collapse-item>

          <!-- 20. 静脉正性肌力支持类型 -->
          <el-collapse-item title="20. 静脉正性肌力支持类型" name="jmzxjl">
            <el-col :span="8">
              <div class="grid-content">
                <el-form-item label="是否使用" class="item">
                  <el-select
                    v-model="formAdd.zlyw_a['静脉正性肌力支持类型']['是否使用']"
                    placeholder="请选择是否使用"
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
          </el-collapse-item>
        </el-collapse>
      </el-tab-pane>

      <!-- 治疗药物(B非心血管药物) -->
      <el-tab-pane label="治疗药物B(非心血管药物)" name="add_seven">
        <el-row>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="1. 非甾体类抗炎药" class="item">
                <el-select
                  v-model="formAdd.zlyw_b['非甾体类抗炎药']"
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
                  v-model="formAdd.zlyw_b['抗糖尿病药物']['是否服用']"
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
                  v-model="formAdd.zlyw_b['抗糖尿病药物']['恩格列净(mg/d)']"
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
                  v-model="formAdd.zlyw_b['抗糖尿病药物']['达格列净(mg/d)']"
                  placeholder="请输入达格列净(mg/d)"
                  maxlength="4"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
        </el-row>

        <el-col :span="8">
          <div class="grid-content">
            <el-form-item label="3. 抗抑郁药" class="item">
              <el-select
                v-model="formAdd.zlyw_b['抗抑郁药']"
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
                v-model="formAdd.zlyw_b['秋水仙碱']"
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
                v-model="formAdd.zlyw_b['甲状腺激素替代治疗']"
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
                v-model="formAdd.zlyw_b['是否参加随机对照临床研究']"
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
      </el-tab-pane>
    </el-tabs>

    <el-form-item>
      <el-button type="primary" @click="submitForm('formAdd')">保存</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
export default {
  name: "RecordAdd",
  props: ["base_id"],
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
      formAdd: {
        name: "",
        hzzz: {
          乏力与疲劳: "",
          "气短/呼吸困难": "",
          "焦虑/抑郁": "",
          活动能力: "",
          自理能力: "",
          日常活动: "",
          其它躯体不适: "",
          生活质量自评: "",
          充血性心力衰竭症状: "",
          心力衰竭症状等级: "",
        },
        shfs: {
          饮酒情况: "",
          吸烟情况: "",
          基础血压低: "",
          基础心率低: "",
          治疗依从性高: "",
          睡眠质量好: "",
          治疗依从性高: "",
          患者本人重视程度高: "",
          患者本人信心: "",
          家属关心程度: "",
          有氧运动: "",
          经济条件: "",
          对社会及生活的情感: "",
          人际关系: "",
          对患病及衰老的态度: "",
          每天进食食盐: "",
          食欲: "",
          "平均每日入水量(ml)": "",
        },
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
        zlyw_a: {
          ACEI: {
            是否使用: "",
            未用: { 原因: "", 症状: "" },
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
              是否达到目标剂量: "",
              未达目标剂量理由: "",
              是否增加剂量: "",
              未增剂量理由: "",
            },
          },
          ARNI: {
            是否使用: "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
              是否达到目标剂量: "",
              未达目标剂量理由: "",
              是否增加剂量: "",
              未增剂量理由: "",
            },
          },
          ARB: {
            是否使用: "",
            未用: { 原因: "", 症状: "" },
            已用: {
              药物名称: "",
              是否达到目标剂量: "",
              未达目标剂量理由: "",
              是否增加剂量: "",
              未增剂量理由: "",
            },
          },
          β受体阻滞剂: {
            是否使用: "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
              是否达到目标剂量: "",
              未达目标剂量理由: "",
              是否增加剂量: "",
              未增剂量理由: "",
            },
          },
          醛固酮受体阻断剂: {
            是否使用: "",
            "有无症状(NYHA分级为I)": "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
            },
          },
          伊伐布雷定: {
            是否使用: "",
            未用: { 原因: "", 症状: "" },
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
            },
          },
          噻嗪类利尿剂: {
            是否使用: "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
            },
          },
          髓袢利尿剂: {
            是否使用: "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
            },
          },
          地高辛: {
            是否使用: "",
            "药物剂量(mg/d)": "",
          },
          芪苈强心胶囊: {
            是否使用: "",
          },
          胺碘酮: {
            是否使用: "",
            "药物剂量(mg/d)": "",
          },
          其他抗心律失常药物: {
            是否使用: "",
          },
          抗血小板药: {
            是否使用: "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
            },
          },
          抗凝药: {
            是否使用: "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
            },
          },
          他汀类药物: {
            是否使用: "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
            },
          },
          二氢吡啶类钙拮抗剂: {
            是否使用: "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
            },
          },
          非二氢吡啶类钙拮抗剂: {
            是否使用: ""
          },
          硝酸酯类药物: {
            是否使用: "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
            },
          },
          静脉正性肌力支持类型: {
            是否使用: ""
          },
        },
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
        患者现状: ["健在", "新的住院，新植入装置，中期非计划随访", "死亡"],
        症状: {
          乏力与疲劳: ["无", "轻度", "明显", "严重", "不适用"],
          "气短/呼吸困难": ["无", "轻度", "明显", "严重", "不适用"],
          活动能力: ["无受限", "降低", "卧床"],
          日常活动: ["无困难", "存在一定困难", "不能正常进行"],
          自理能力: ["能够自理", "穿衣、洗澡部分困难", "无法自行穿衣、洗澡"],
          其它躯体不适: ["无不适", "轻度不适", "严重不适"],
          "焦虑/抑郁": ["无焦虑和抑郁", "轻度焦虑或抑郁", "严重焦虑或抑郁"],
          生活质量自评: "",
          充血性心力衰竭症状: [
            "无",
            "呼吸急促",
            "端坐呼吸",
            "夜间阵发性呼吸困难",
            "乏力",
          ],
          心力衰竭症状等级: [
            "心功能I级",
            "心功能II级",
            "心功能III级",
            "心功能IV级",
          ],
        },
        生活方式: {
          饮酒情况: ["从不", "已戒酒", "? g/天", "偶尔"],
          吸烟情况: ["从不", "已戒酒", "? 支/天", "偶尔"],
          基础血压低: [],
          基础心率低: [],
          治疗依从性高: [],
          患者本人重视程度高: [],
          患者本人信心: ["能治好", "能缓解", "不能缓解", "完全没有希望"],
          家属关心程度: ["很关心", "一般关心", "不太关心", "不关心"],
          有氧运动: [
            "频繁（每周5~7天）",
            "较少（3~4天）",
            "很少（1~2天）",
            "不运动",
          ],
          经济条件: ["很好满足", "刚好满足", "不能满足"],
          对社会及生活的情感: ["乐观", "不满", "愤愤不平", "悲观", "其他"],
          人际关系: ["愉快", "一般", "紧张"],
          对患病及衰老的态度: [
            "能理解和接受",
            "感到忧虑",
            "完全不能理解和接受",
          ],
          每天进食食盐: ["小于6克", "6~10克", "大于10克"],
          食欲: ["好", "一般", "不好", "差"],
        },
        体征与体格检查: {},
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
      sflxList: [
        { key: "WEEK", value: "周随访" },
        { key: "MONTH", value: "月随访" },
        { key: "HALF_YEAR", value: "半年随访" },
        { key: "RANDOM", value: "随机随访" },
      ],
      sfxsList: [
        { key: "DH", value: "电话" },
        { key: "MZ", value: "门诊" },
        { key: "ZCZY", value: "再次住院" },
      ],
      rules: {
        record_type: [
          { required: true, message: "请选择随访类型", trigger: "change" },
        ],
        vist_time: [
          { required: true, message: "请选择随访时间", trigger: "change" },
        ],
        sfxs: [
          { required: true, message: "请选择随访形式", trigger: "change" },
        ],
      },
    };
  },
  methods: {
    // 吸烟情况
    queryXySearch(queryString, cb) {
      var querydata = this.template_data.生活方式.吸烟情况;
      var results = queryString
        ? querydata.filter(this.createFilter(querydata, queryString))
        : querydata;
      var resultArr = [];
      for (let item of results) {
        resultArr.push({ value: item });
      }
      cb(resultArr);
    },
    // 饮酒情况
    queryYjSearch(queryString, cb) {
      var querydata = this.template_data.生活方式.饮酒情况;
      var results = queryString
        ? querydata.filter(this.createFilter(querydata, queryString))
        : querydata;
      var resultArr = [];
      for (let item of results) {
        resultArr.push({ value: item });
      }
      cb(resultArr);
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
    createFilter(curArr, queryString) {
      return (curArr) => {
        return curArr.toLowerCase().indexOf(queryString.toLowerCase()) === 0;
      };
    },
    resetForm() {},
    submitForm(formName) {
      this.formAdd.base_id = this.base_id;
      // var formData = JSON.stringify(this.formAdd);
      this.$refs[formName].validate((valid) => {
        if (valid) {
          // 新增记录；需验证随访类型、随访日期必填
          this.postRequest("/visit/record/", this.formAdd).then((resp) => {
            if (resp) {
              this.$emit("finishSave", true);
            }
          });
        } else {
          alert("提交信息校验未通过!");
          // console.log("error submit!!");
          return false;
        }
      });
    },
    handleSelect(item) {
      console.log(item);
    },
    handleIconClick(ev) {
      console.log(ev);
    },
  },
  mounted() {
    // 初始化数组
    this.template_data.生活方式.基础血压低 = this.base_selarr;
    this.template_data.生活方式.基础心率低 = this.base_selarr;
    this.template_data.生活方式.治疗依从性高 = this.base_selarr;
    this.template_data.生活方式.患者本人重视程度高 = this.base_selarr;
  },
  watch: {},
};
</script>
<style>
/* .my-autocomplete {
  li {
    line-height: normal;
    padding: 7px;

    .name {
      text-overflow: ellipsis;
      overflow: hidden;
    }
    .addr {
      font-size: 12px;
      color: #b4b4b4;
    }

    .highlighted .addr {
      color: #ddd;
    }
  }
} */

el-tag {
  margin-right: 5px;
  margin-bottom: 10px;
}
</style>
