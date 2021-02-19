<template>
  <div>
    <el-form
      ref="formZlywA"
      :model="formZlywA"
      label-width="180px"
      label-position="left"
      :inline="true"
    >
 
       <!-- 治疗药物A(心血管药物) -->
        <!-- 血管紧张素转化为酶抑制剂（ACEI） -->
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>1. 血管紧张素转化为酶抑制剂（ACEI）</span>
          </div>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="是否使用" class="item">
                <el-select
                  v-model="formZlywA.zlyw_a.ACEI['是否使用']"
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
                  v-model="formZlywA.zlyw_a.ACEI['未用']['原因']"
                  :fetch-suggestions="queryReasonASearch"
                  placeholder="请输入未用原因"
                >
                  <i
                    class="el-icon-edit el-input__icon"
                    slot="suffix"
                  ></i>
                  <template slot-scope="props">
                    <div class="name">{{ props.item.value }}</div>
                  </template>
                </el-autocomplete>
              </el-form-item>
            </div>
          </el-col>

          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="症状" class="item">
                <el-select
                  v-model="formZlywA.zlyw_a.ACEI['未用']['症状']"
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
                  v-model="formZlywA.zlyw_a.ACEI['已用']['药物名称']"
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
                  v-model="formZlywA.zlyw_a.ACEI['已用']['药物剂量(mg/d)']"
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
                  v-model="formZlywA.zlyw_a.ACEI['已用']['是否达到目标剂量']"
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
                  v-model="formZlywA.zlyw_a.ACEI['已用']['未达目标剂量理由']"
                  placeholder="请输入未达到目标剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物是否增加剂量" class="item">
                <el-select
                  v-model="formZlywA.zlyw_a.ACEI['已用']['是否增加剂量']"
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
                  v-model="formZlywA.zlyw_a.ACEI['已用']['未增剂量理由']"
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
                  v-model="formZlywA.zlyw_a.ARNI['是否使用']"
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
                  v-model="formZlywA.zlyw_a.ARNI['已用']['药物名称']"
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
                  v-model="formZlywA.zlyw_a.ARNI['已用']['药物剂量(mg/d)']"
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
                  v-model="formZlywA.zlyw_a.ARNI['已用']['是否达到目标剂量']"
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
                  v-model="formZlywA.zlyw_a.ARNI['已用']['未达目标剂量理由']"
                  placeholder="请输入未达到目标剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物是否增加剂量" class="item">
                <el-select
                  v-model="formZlywA.zlyw_a.ARNI['已用']['是否增加剂量']"
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
                  v-model="formZlywA.zlyw_a.ARNI['已用']['未增剂量理由']"
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
                  v-model="formZlywA.zlyw_a.ARB['是否使用']"
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
                  v-model="formZlywA.zlyw_a.ARB['未用']['原因']"
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
                  v-model="formZlywA.zlyw_a.ARB['未用']['症状']"
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
                  v-model="formZlywA.zlyw_a.ARB['已用']['药物名称']"
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
                  v-model="formZlywA.zlyw_a.ARB['已用']['药物剂量(mg/d)']"
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
                  v-model="formZlywA.zlyw_a.ARB['已用']['是否达到目标剂量']"
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
                  v-model="formZlywA.zlyw_a.ARB['已用']['未达目标剂量理由']"
                  placeholder="请输入未达到目标剂量理由"
                ></el-input>
              </el-form-item>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content">
              <el-form-item label="药物是否增加剂量" class="item">
                <el-select
                  v-model="formZlywA.zlyw_a.ARB['已用']['是否增加剂量']"
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
                  v-model="formZlywA.zlyw_a.ARB['已用']['未增剂量理由']"
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
                  v-model="formZlywA.zlyw_a['β受体阻滞剂']['是否使用']"
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
                  v-model="formZlywA.zlyw_a['β受体阻滞剂']['已用']['药物名称']"
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
                    formZlywA.zlyw_a['β受体阻滞剂']['已用']['药物剂量(mg/d)']
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
                    formZlywA.zlyw_a['β受体阻滞剂']['已用']['是否达到目标剂量']
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
                    formZlywA.zlyw_a['β受体阻滞剂']['已用']['未达目标剂量理由']
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
                    formZlywA.zlyw_a['β受体阻滞剂']['已用']['是否增加剂量']
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
                    formZlywA.zlyw_a['β受体阻滞剂']['已用']['未增剂量理由']
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
                  v-model="formZlywA.zlyw_a['醛固酮受体阻断剂']['是否使用']"
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
                    formZlywA.zlyw_a['醛固酮受体阻断剂']['已用']['药物名称']
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
                    formZlywA.zlyw_a['醛固酮受体阻断剂']['已用']['药物剂量(mg/d)']
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
                    formZlywA.zlyw_a['醛固酮受体阻断剂']['有无症状(NYHA分级为I)']
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
                  v-model="formZlywA.zlyw_a['伊伐布雷定']['是否使用']"
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
                  v-model="formZlywA.zlyw_a['伊伐布雷定']['未用']['原因']"
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
                  v-model="formZlywA.zlyw_a['伊伐布雷定']['未用']['症状']"
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
                  v-model="formZlywA.zlyw_a['伊伐布雷定']['已用']['药物名称']"
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
                    formZlywA.zlyw_a['伊伐布雷定']['已用']['药物剂量(mg/d)']
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
                    v-model="formZlywA.zlyw_a['噻嗪类利尿剂']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['噻嗪类利尿剂']['已用']['药物名称']"
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
                      formZlywA.zlyw_a['噻嗪类利尿剂']['已用']['药物剂量(mg/d)']
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
                    v-model="formZlywA.zlyw_a['髓袢利尿剂']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['髓袢利尿剂']['已用']['药物名称']"
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
                      formZlywA.zlyw_a['髓袢利尿剂']['已用']['药物剂量(mg/d)']
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
                    v-model="formZlywA.zlyw_a['地高辛']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['地高辛']['药物剂量(mg/d)']"
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
                    v-model="formZlywA.zlyw_a['芪苈强心胶囊']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['胺碘酮']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['胺碘酮']['药物剂量(mg/d)']"
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
                    v-model="formZlywA.zlyw_a['其他抗心律失常药物']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['抗血小板药']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['抗血小板药']['已用']['药物名称']"
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
                    v-model="formZlywA.zlyw_a['抗血小板药']['药物剂量(mg/d)']"
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
                    v-model="formZlywA.zlyw_a['抗凝药']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['抗凝药']['已用']['药物名称']"
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
                    v-model="formZlywA.zlyw_a['抗凝药']['药物剂量(mg/d)']"
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
                    v-model="formZlywA.zlyw_a['他汀类药物']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['他汀类药物']['已用']['药物名称']"
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
                    v-model="formZlywA.zlyw_a['他汀类药物']['药物剂量(mg/d)']"
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
                    v-model="formZlywA.zlyw_a['二氢吡啶类钙拮抗剂']['是否使用']"
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
                      formZlywA.zlyw_a['二氢吡啶类钙拮抗剂']['已用']['药物名称']
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
                      formZlywA.zlyw_a['二氢吡啶类钙拮抗剂']['药物剂量(mg/d)']
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
                    v-model="formZlywA.zlyw_a['非二氢吡啶类钙拮抗剂']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['硝酸酯类药物']['是否使用']"
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
                    v-model="formZlywA.zlyw_a['硝酸酯类药物']['已用']['药物名称']"
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
                    v-model="formZlywA.zlyw_a['硝酸酯类药物']['药物剂量(mg/d)']"
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
                    v-model="formZlywA.zlyw_a['静脉正性肌力支持类型']['是否使用']"
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

      <!-- <el-tag style="margin-bottom: 10px" type="danger"
        >* 4. 坐位动脉血压输入：收缩压/舒张压，*/* mmHg！</el-tag
      >
      <br />
      <el-tag style="margin-bottom: 10px" type="danger"
        >* 8. 颈静脉压升高体征即：颈静脉充盈！</el-tag
      >
      <br /> -->
      <el-form-item>
        <el-button type="primary" @click="submitForm('formZlywA')"
          >保存</el-button
        >
        <el-button @click="resetForm()">重置</el-button>

      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "RecordZlywA",
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
      formZlywA: {
        record_id: "",
        name: "",
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
              药物剂量: "",
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
              药物剂量: "",
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
              "是否使用":""
          },
          硝酸酯类药物: {
            是否使用: "",
            已用: {
              药物名称: "",
              "药物剂量(mg/d)": "",
            },
          },
          静脉正性肌力支持类型: {
              "是否使用":""
          },
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
            this.formZlywA.zlyw_a["ACEI"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["ACEI"]["未用"]["原因"] = null;
          this.formZlywA.zlyw_a["ACEI"]["未用"]["症状"] = null;
          this.formZlywA.zlyw_a["ACEI"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["ACEI"]["已用"]["药物剂量(mg/d)"] = null;
          this.formZlywA.zlyw_a["ACEI"]["已用"]["是否达到目标剂量"] = null;
          this.formZlywA.zlyw_a["ACEI"]["已用"]["未达目标剂量理由"] = null;
          this.formZlywA.zlyw_a["ACEI"]["已用"]["是否增加剂量"] = null;
          this.formZlywA.zlyw_a["ACEI"]["已用"]["未增剂量理由"] = null;

          this.formZlywA.zlyw_a["ARNI"]["是否使用"] = null;
          this.formZlywA.zlyw_a["ARNI"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["ARNI"]["已用"]["药物剂量(mg/d)"] = null;
          this.formZlywA.zlyw_a["ARNI"]["已用"]["是否达到目标剂量"] = null;
          this.formZlywA.zlyw_a["ARNI"]["已用"]["未达目标剂量理由"] = null;
          this.formZlywA.zlyw_a["ARNI"]["已用"]["是否增加剂量"] = null;
          this.formZlywA.zlyw_a["ARNI"]["已用"]["未增剂量理由"] = null;
          
            this.formZlywA.zlyw_a["ARB"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["ARB"]["未用"]["原因"] = null;
          this.formZlywA.zlyw_a["ARB"]["未用"]["症状"] = null;
          this.formZlywA.zlyw_a["ARB"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["ARB"]["已用"]["是否达到目标剂量"] = null;
          this.formZlywA.zlyw_a["ARB"]["已用"]["未达目标剂量理由"] = null;
          this.formZlywA.zlyw_a["ARB"]["已用"]["是否增加剂量"] = null;
          this.formZlywA.zlyw_a["ARB"]["已用"]["未增剂量理由"] = null;

            this.formZlywA.zlyw_a["β受体阻滞剂"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["药物剂量(mg/d)"] = null;
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["是否达到目标剂量"] = null;
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["未达目标剂量理由"] = null;
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["是否增加剂量"] = null;
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["未增剂量理由"] = null;  

            this.formZlywA.zlyw_a["醛固酮受体阻断剂"]["是否使用"]  = null;
            this.formZlywA.zlyw_a["醛固酮受体阻断剂"]["有无症状(NYHA分级为I)"]  = null;
          this.formZlywA.zlyw_a["醛固酮受体阻断剂"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["醛固酮受体阻断剂"]["已用"]["药物剂量(mg/d)"] = null;

            this.formZlywA.zlyw_a["伊伐布雷定"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["伊伐布雷定"]["未用"]["原因"] = null;
          this.formZlywA.zlyw_a["伊伐布雷定"]["未用"]["症状"] = null;
          this.formZlywA.zlyw_a["伊伐布雷定"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["伊伐布雷定"]["已用"]["药物剂量(mg/d)"] = null;

          this.formZlywA.zlyw_a["噻嗪类利尿剂"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["噻嗪类利尿剂"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["噻嗪类利尿剂"]["已用"]["药物剂量(mg/d)"] = null;

        this.formZlywA.zlyw_a["髓袢利尿剂"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["髓袢利尿剂"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["髓袢利尿剂"]["已用"]["药物剂量(mg/d)"] = null;

            this.formZlywA.zlyw_a["地高辛"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["地高辛"]["药物剂量(mg/d)"] = null;

            this.formZlywA.zlyw_a["芪苈强心胶囊"]["是否使用"]  = null;

            this.formZlywA.zlyw_a["胺碘酮"]["是否使用"]  = null;
            this.formZlywA.zlyw_a["胺碘酮"]["药物剂量(mg/d)"]  = null;

            this.formZlywA.zlyw_a["其他抗心律失常药物"]["是否使用"]  = null;

            this.formZlywA.zlyw_a["抗血小板药"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["抗血小板药"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["抗血小板药"]["已用"]["药物剂量(mg/d)"] = null;

            this.formZlywA.zlyw_a["抗凝药"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["抗凝药"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["抗凝药"]["已用"]["药物剂量(mg/d)"] = null;

            this.formZlywA.zlyw_a["他汀类药物"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["他汀类药物"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["他汀类药物"]["已用"]["药物剂量(mg/d)"] = null;

            this.formZlywA.zlyw_a["二氢吡啶类钙拮抗剂"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["二氢吡啶类钙拮抗剂"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["二氢吡啶类钙拮抗剂"]["已用"]["药物剂量(mg/d)"] = null;

            this.formZlywA.zlyw_a["非二氢吡啶类钙拮抗剂"]["是否使用"]  = null;

            this.formZlywA.zlyw_a["硝酸酯类药物"]["是否使用"]  = null;
          this.formZlywA.zlyw_a["硝酸酯类药物"]["已用"]["药物名称"] = null;
          this.formZlywA.zlyw_a["硝酸酯类药物"]["已用"]["药物剂量(mg/d)"] = null;

            this.formZlywA.zlyw_a["静脉正性肌力支持类型"]["是否使用"]  = null;
    },
    initformZlywA() {},
    loadZlywAData() {
      console.log("------loadZlywAData-------");
      this.resetForm();
      let record_id = this.record_id;
      // 读取数据
      this.getRequest("/visit/record/" + record_id).then((resp) => {
      
console.log("------resp-------", resp);
        if (resp.zlyw_a) {
            console.log("------resp.zlyw_a-------", resp.zlyw_a);
          this.formZlywA.zlyw_a["ACEI"]["是否使用"]  = JSON.parse(resp.zlyw_a)["ACEI"]["是否使用"];
          this.formZlywA.zlyw_a["ACEI"]["未用"]["原因"] = JSON.parse(resp.zlyw_a)["ACEI"]["未用"]["原因"];
          this.formZlywA.zlyw_a["ACEI"]["未用"]["症状"] = JSON.parse(resp.zlyw_a)["ACEI"]["未用"]["症状"];
          this.formZlywA.zlyw_a["ACEI"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["ACEI"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["ACEI"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["ACEI"]["已用"]["药物剂量(mg/d)"];
          this.formZlywA.zlyw_a["ACEI"]["已用"]["是否达到目标剂量"] = JSON.parse(resp.zlyw_a)["ACEI"]["已用"]["是否达到目标剂量"];
          this.formZlywA.zlyw_a["ACEI"]["已用"]["未达目标剂量理由"] = JSON.parse(resp.zlyw_a)["ACEI"]["已用"]["未达目标剂量理由"];
          this.formZlywA.zlyw_a["ACEI"]["已用"]["是否增加剂量"] = JSON.parse(resp.zlyw_a)["ACEI"]["已用"]["是否增加剂量"];
          this.formZlywA.zlyw_a["ACEI"]["已用"]["未增剂量理由"] = JSON.parse(resp.zlyw_a)["ACEI"]["已用"]["未增剂量理由"];

          this.formZlywA.zlyw_a["ARNI"]["是否使用"] = JSON.parse(resp.zlyw_a)["ARNI"]["是否使用"];
          this.formZlywA.zlyw_a["ARNI"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["ARNI"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["ARNI"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["ARNI"]["已用"]["药物剂量(mg/d)"];
          this.formZlywA.zlyw_a["ARNI"]["已用"]["是否达到目标剂量"] = JSON.parse(resp.zlyw_a)["ARNI"]["已用"]["是否达到目标剂量"];
          this.formZlywA.zlyw_a["ARNI"]["已用"]["未达目标剂量理由"] = JSON.parse(resp.zlyw_a)["ARNI"]["已用"]["未达目标剂量理由"];
          this.formZlywA.zlyw_a["ARNI"]["已用"]["是否增加剂量"] = JSON.parse(resp.zlyw_a)["ARNI"]["已用"]["是否增加剂量"];
          this.formZlywA.zlyw_a["ARNI"]["已用"]["未增剂量理由"] = JSON.parse(resp.zlyw_a)["ARNI"]["已用"]["未增剂量理由"];
          
            this.formZlywA.zlyw_a["ARB"]["是否使用"]  = JSON.parse(resp.zlyw_a)["ARB"]["是否使用"];
          this.formZlywA.zlyw_a["ARB"]["未用"]["原因"] = JSON.parse(resp.zlyw_a)["ARB"]["未用"]["原因"];
          this.formZlywA.zlyw_a["ARB"]["未用"]["症状"] = JSON.parse(resp.zlyw_a)["ARB"]["未用"]["症状"];
          this.formZlywA.zlyw_a["ARB"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["ARB"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["ARB"]["已用"]["是否达到目标剂量"] = JSON.parse(resp.zlyw_a)["ARB"]["已用"]["是否达到目标剂量"];
          this.formZlywA.zlyw_a["ARB"]["已用"]["未达目标剂量理由"] = JSON.parse(resp.zlyw_a)["ARB"]["已用"]["未达目标剂量理由"];
          this.formZlywA.zlyw_a["ARB"]["已用"]["是否增加剂量"] = JSON.parse(resp.zlyw_a)["ARB"]["已用"]["是否增加剂量"];
          this.formZlywA.zlyw_a["ARB"]["已用"]["未增剂量理由"] = JSON.parse(resp.zlyw_a)["ARB"]["已用"]["未增剂量理由"];

            this.formZlywA.zlyw_a["β受体阻滞剂"]["是否使用"]  = JSON.parse(resp.zlyw_a)["β受体阻滞剂"]["是否使用"];
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["β受体阻滞剂"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["β受体阻滞剂"]["已用"]["药物剂量(mg/d)"];
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["是否达到目标剂量"] = JSON.parse(resp.zlyw_a)["β受体阻滞剂"]["已用"]["是否达到目标剂量"];
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["未达目标剂量理由"] = JSON.parse(resp.zlyw_a)["β受体阻滞剂"]["已用"]["未达目标剂量理由"];
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["是否增加剂量"] = JSON.parse(resp.zlyw_a)["β受体阻滞剂"]["已用"]["是否增加剂量"];
          this.formZlywA.zlyw_a["β受体阻滞剂"]["已用"]["未增剂量理由"] = JSON.parse(resp.zlyw_a)["β受体阻滞剂"]["已用"]["未增剂量理由"];  

            this.formZlywA.zlyw_a["醛固酮受体阻断剂"]["是否使用"]  = JSON.parse(resp.zlyw_a)["醛固酮受体阻断剂"]["是否使用"];
            this.formZlywA.zlyw_a["醛固酮受体阻断剂"]["有无症状(NYHA分级为I)"]  = JSON.parse(resp.zlyw_a)["醛固酮受体阻断剂"]["有无症状(NYHA分级为I)"];
          this.formZlywA.zlyw_a["醛固酮受体阻断剂"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["醛固酮受体阻断剂"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["醛固酮受体阻断剂"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["醛固酮受体阻断剂"]["已用"]["药物剂量(mg/d)"];

            this.formZlywA.zlyw_a["伊伐布雷定"]["是否使用"]  = JSON.parse(resp.zlyw_a)["伊伐布雷定"]["是否使用"];
          this.formZlywA.zlyw_a["伊伐布雷定"]["未用"]["原因"] = JSON.parse(resp.zlyw_a)["伊伐布雷定"]["未用"]["原因"];
          this.formZlywA.zlyw_a["伊伐布雷定"]["未用"]["症状"] = JSON.parse(resp.zlyw_a)["伊伐布雷定"]["未用"]["症状"];
          this.formZlywA.zlyw_a["伊伐布雷定"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["伊伐布雷定"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["伊伐布雷定"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["伊伐布雷定"]["已用"]["药物剂量(mg/d)"];

          this.formZlywA.zlyw_a["噻嗪类利尿剂"]["是否使用"]  = JSON.parse(resp.zlyw_a)["噻嗪类利尿剂"]["是否使用"];
          this.formZlywA.zlyw_a["噻嗪类利尿剂"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["噻嗪类利尿剂"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["噻嗪类利尿剂"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["噻嗪类利尿剂"]["已用"]["药物剂量(mg/d)"];

        this.formZlywA.zlyw_a["髓袢利尿剂"]["是否使用"]  = JSON.parse(resp.zlyw_a)["髓袢利尿剂"]["是否使用"];
          this.formZlywA.zlyw_a["髓袢利尿剂"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["髓袢利尿剂"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["髓袢利尿剂"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["髓袢利尿剂"]["已用"]["药物剂量(mg/d)"];

            this.formZlywA.zlyw_a["地高辛"]["是否使用"]  = JSON.parse(resp.zlyw_a)["地高辛"]["是否使用"];
          this.formZlywA.zlyw_a["地高辛"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["地高辛"]["药物剂量(mg/d)"];

            this.formZlywA.zlyw_a["芪苈强心胶囊"]["是否使用"]  = JSON.parse(resp.zlyw_a)["芪苈强心胶囊"]["是否使用"];

            this.formZlywA.zlyw_a["胺碘酮"]["是否使用"]  = JSON.parse(resp.zlyw_a)["胺碘酮"]["是否使用"];
            this.formZlywA.zlyw_a["胺碘酮"]["药物剂量(mg/d)"]  = JSON.parse(resp.zlyw_a)["胺碘酮"]["药物剂量(mg/d)"];

            this.formZlywA.zlyw_a["其他抗心律失常药物"]["是否使用"]  = JSON.parse(resp.zlyw_a)["其他抗心律失常药物"]["是否使用"];

            this.formZlywA.zlyw_a["抗血小板药"]["是否使用"]  = JSON.parse(resp.zlyw_a)["抗血小板药"]["是否使用"];
          this.formZlywA.zlyw_a["抗血小板药"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["抗血小板药"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["抗血小板药"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["抗血小板药"]["已用"]["药物剂量(mg/d)"];

            this.formZlywA.zlyw_a["抗凝药"]["是否使用"]  = JSON.parse(resp.zlyw_a)["抗凝药"]["是否使用"];
          this.formZlywA.zlyw_a["抗凝药"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["抗凝药"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["抗凝药"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["抗凝药"]["已用"]["药物剂量(mg/d)"];

            this.formZlywA.zlyw_a["他汀类药物"]["是否使用"]  = JSON.parse(resp.zlyw_a)["他汀类药物"]["是否使用"];
          this.formZlywA.zlyw_a["他汀类药物"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["他汀类药物"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["他汀类药物"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["他汀类药物"]["已用"]["药物剂量(mg/d)"];

            this.formZlywA.zlyw_a["二氢吡啶类钙拮抗剂"]["是否使用"]  = JSON.parse(resp.zlyw_a)["二氢吡啶类钙拮抗剂"]["是否使用"];
          this.formZlywA.zlyw_a["二氢吡啶类钙拮抗剂"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["二氢吡啶类钙拮抗剂"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["二氢吡啶类钙拮抗剂"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["二氢吡啶类钙拮抗剂"]["已用"]["药物剂量(mg/d)"];

            this.formZlywA.zlyw_a["非二氢吡啶类钙拮抗剂"]["是否使用"]  = JSON.parse(resp.zlyw_a)["非二氢吡啶类钙拮抗剂"]["是否使用"];

            this.formZlywA.zlyw_a["硝酸酯类药物"]["是否使用"]  = JSON.parse(resp.zlyw_a)["硝酸酯类药物"]["是否使用"];
          this.formZlywA.zlyw_a["硝酸酯类药物"]["已用"]["药物名称"] = JSON.parse(resp.zlyw_a)["硝酸酯类药物"]["已用"]["药物名称"];
          this.formZlywA.zlyw_a["硝酸酯类药物"]["已用"]["药物剂量(mg/d)"] = JSON.parse(resp.zlyw_a)["硝酸酯类药物"]["已用"]["药物剂量(mg/d)"];

            this.formZlywA.zlyw_a["静脉正性肌力支持类型"]["是否使用"]  = JSON.parse(resp.zlyw_a)["静脉正性肌力支持类型"]["是否使用"];

        }
      });
    },
    submitForm() {
      this.formZlywA.record_id = this.record_id;
      var formData = JSON.stringify(this.formZlywA);
      console.log("this.formZlywA", this.formZlywA);
      this.putRequest("/visit/record/zlywA/", this.formZlywA).then((resp) => {
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
    this.loadZlywAData();
  },
  watch: {
    record_id: function (newData, oldData) {},
  },
};
</script>