<template>
  <div>

    <el-form
      :model="baseForm"
      :rules="rules"
      ref="baseForm"
      label-width="100px"
      class="demo-baseForm">
      <el-form-item label="基线名称" prop="base_name">
        <el-input v-model="baseForm.base_name"></el-input>
      </el-form-item>
      <!-- <el-form-item label="项目" prop="project_id">
        <el-select v-model="baseForm.project_id" placeholder="请选择基线建立区域">
          <el-option label="402室" value="shanghai"></el-option>
          <el-option label="403室" value="beijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="基线区域" prop="address">
        <el-select v-model="baseForm.address" placeholder="请选择基线建立区域">
          <el-option label="402室" value="shanghai"></el-option>
          <el-option label="403室" value="beijing"></el-option>
        </el-select>
      </el-form-item> -->
      <el-form-item label="基线时间" required>
        <el-col :span="5">
          <el-form-item prop="base_time">
            <el-date-picker
              type="date"
              placeholder="选择日期"
              v-model="baseForm.base_time"
              style="width: 100%;"
            ></el-date-picker>
          </el-form-item>
        </el-col>
      </el-form-item>  
      
      <el-form-item label="备注" prop="remark">
        <el-input type="textarea" v-model="baseForm.remark"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submitForm('baseForm')">保存</el-button>
        <el-button @click="resetForm('baseForm')">重置</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  props: ['base_id'],
  data() {
    return {
      baseForm: {
        base_name: "",
        region: "",
        date1: "",
        date2: "",
        delivery: false,
        type: [],
        resource: "",
        remark: ""
      },
      rules: {
        base_name: [
          { required: true, message: "请输入基线名称", trigger: "blur" },
          { min: 3, max: 5, message: "长度在 3 到 5 个字符", trigger: "blur" }
        ],
        region: [
          { required: true, message: "请选择基线区域", trigger: "change" }
        ],
        date1: [
          {
            type: "date",
            required: true,
            message: "请选择日期",
            trigger: "change"
          }
        ],
        date2: [
          {
            type: "date",
            required: true,
            message: "请选择时间",
            trigger: "change"
          }
        ],
        remark: [{ required: true, message: "请填写备注", trigger: "blur" }]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
};
</script>

<style>
.addPosInput {
  width: 300px;
  margin-right: 8px;
}

.posManaMain {
  margin-top: 10px;
}

.updatePosInput {
  width: 200px;
  margin-left: 8px;
}
</style>>