<template>
  <div>
    <div>
      <el-input
        placeholder="访视基线"
        prefix-icon="el-icon-search"
        style="width:300px;margin-right:10px;"
        v-model="base_name" :disabled="true"
      ></el-input>

      <el-button icon="el-icon-search" type="primary" @click="queryRecords">搜索</el-button>
      <el-button icon="el-icon-plus" type="primary" @click="addRecord">添加访视记录</el-button>
      <el-button icon="el-icon-down" type="primary" @click="prev">返回</el-button>
    </div>
    <hr />
    <div style="margin-top:10px;">
      <el-table style="width: 100%" :data="records" stripe border 
       v-loading="loading"
       element-loading-text="正在加载...">
        <el-table-column type="selection" width="55"></el-table-column>
        <el-table-column prop="patient_name" label="姓名" align="left" fixed width="90"></el-table-column>
        <el-table-column prop="patient_id" label="证件号码" align="left" width="150"></el-table-column>
        <el-table-column prop="vist_time" label="访视日期" :formatter="dateFormatter" align="left" width="115" ></el-table-column>
        <el-table-column prop="record_type"   label="访视类型" align="left" width="150" :formatter="fslxFormat"></el-table-column>
        <el-table-column prop="sfxs" label="随访形式" align="left" width="120" :formatter="sfxsFormat"></el-table-column>
        <el-table-column prop="nation.name" label="创建人" align="left" width="100"></el-table-column>
        <el-table-column prop="nativePlace" label="创建时间" align="left" width="140"></el-table-column>
        <el-table-column label="操作" width="200">
          <template slot-scope="scope">
            <el-button style="padding:3px;" size="mini" @click="showEditRecordView(scope.row)">具体内容</el-button>
            <!-- <el-button style="padding:3px;" size="mini" type="primary">建档</el-button> -->
            <el-button
              style="padding:3px;"
              size="mini"
              type="danger"
              @click="deleteRecord(scope.row)"
            >删除</el-button>
          </template>
        </el-table-column>


      </el-table>
      <div style="display:flex;justify-content:flex-end">
                    <el-pagination
                        background
                        @current-change="currentChange"
                        @size-change = "sizeChange"
                        layout="sizes, prev, pager, next, jumper, ->, total, slot"
                        :total="total">
                        </el-pagination>
                </div>
    </div>

    <el-dialog title="修改随访" width="70%" :visible.sync="dialogVisible">
      <el-tabs v-model="activeUpdate" type="card">
        <el-tab-pane label="随访基本信息" name="first" v-if="dialogVisible">
          <RecordBase v-bind:record_id="recordId"></RecordBase>
        </el-tab-pane>
        <el-tab-pane label="随访症状" name="second" v-if="dialogVisible">
          <RecordZz v-bind:record_id="recordId"></RecordZz>
        </el-tab-pane>
        <el-tab-pane label="生活方式" name="three" v-if="dialogVisible">
          <RecordShfs v-bind:record_id="recordId"></RecordShfs>
        </el-tab-pane>
        <el-tab-pane label="体征与体格检查" name="four" v-if="dialogVisible">
          <RecordTzytg v-bind:record_id="recordId"></RecordTzytg>
        </el-tab-pane>
         <el-tab-pane label="检测结果（电话随访可不填）" name="five" v-if="dialogVisible">
          <RecordJcjg v-bind:record_id="recordId"></RecordJcjg>
        </el-tab-pane>
        <el-tab-pane label="治疗药物A(心血管药物)" name="six" v-if="dialogVisible">
          <RecordZlywA v-bind:record_id="recordId"></RecordZlywA>
        </el-tab-pane>
        <el-tab-pane label="治疗药物B(非心血管药物)" name="seven" v-if="dialogVisible">
          <RecordZlywB v-bind:record_id="recordId"></RecordZlywB>
        </el-tab-pane>
      </el-tabs>
    </el-dialog>

    <el-dialog title="新增随访" width="70%" :visible.sync="add_dialogVisible">
      <RecordAdd v-bind:base_id="base_id" @finishSave="getSave"></RecordAdd>
    </el-dialog>
    
  </div>
</template>

<script>
import RecordBase from "../../components/pat/basic/RecordBase";
import RecordZz from "../../components/pat/basic/RecordZz";
import RecordAdd from "../../components/pat/basic/RecordAdd";
import RecordShfs from "../../components/pat/basic/RecordShfs";
import RecordTzytg from "../../components/pat/basic/RecordTzytg";
import RecordJcjg from "../../components/pat/basic/RecordJcjg";
import RecordZlywA from "../../components/pat/basic/RecordZlywA";
import RecordZlywB from "../../components/pat/basic/RecordZlywB";

export default {
  name: "patVisitRecord",
  data() {
    return {
      activeUpdate: "second",
      loading: false,
      total:0,
      page:1,
      size:10,
      base_id:"",
      base_name:"",
      recordId: "",
      records: [],
      record: [],
      title: "",
      dialogVisible: false,
      add_dialogVisible: false,
      sflxDic: {"WEEK":"周随访","MONTH": "月随访","HALF_YEAR":"半年随访","RANDOM":"随机随访"},
      sfxsDic: {"DH":"电话","MZ":"门诊","ZCZY":"再次住院"}
    };
  },
  components: {
    RecordBase,
    RecordZz,
    RecordAdd,
    RecordShfs,
    RecordTzytg,
    RecordJcjg,
    RecordZlywA,
    RecordZlywB
  },
  methods: {
    getSave(msg){
      // 获取子组件保存后触发的值
      if(msg){
        this.add_dialogVisible = false;
      }
      this.initRecords();
    },
    addRecord() {
      // 检查基线 是否存在
      if (this.base_id) {
        // 不为空
        this.add_dialogVisible = true;
      } else {
        // 为空
        this.$alert("基线不能为空！", "提示", {
          confirmButtonText: "确定",
        //   callback: action => {
        //     this.$message({
        //       type: "info",
        //       message: `action: ${action}`
        //     });
        //   }
        });
      }
    },
    showEditRecordView(data) {
      this.title = "编辑随访信息";
      this.record = data;
      this.recordId = data.record_id;
      this.dialogVisible = true;
      // this.$refs.recordZz.loadZzData();
    },
    deleteRecord(data) {
      this.$confirm("即将删除, 是否继续?", "提示", {
        confirmButtonText: "确定",
        cancelButtonText: "取消",
        type: "warning"
      })
        .then(() => {
          this.delRequest("/visit/record/" + data.record_id).then(resp => {
            if (resp) this.initRecords();
          });
        })
        .catch(() => {
          this.$message({
            type: "info",
            message: "已取消删除"
          });
        });
    },
    initRecords() {
      this.loading = true
      this.getRequest('/visit/recordsByBase/?page='+this.page+"&size="+this.size+'&base_id='+this.base_id).then(resp=>{
          if(resp){
              this.loading=false
              this.records = resp.data
              this.total = resp.total
          }
      })

    },
    queryRecords(){
        this.page = 1 
        this.initRecords()
    },
    currentChange(currentPage){
              this.page = currentPage
              this.initRecords()
         },
         sizeChange(currentSize){
             this.size=currentSize
             this.initRecords()
         },
   dateFormatter (row, column) {
       let datetime = row[column.property];
       if(datetime){
           datetime = new Date(datetime);
           let y = datetime.getFullYear() + '-';
           let mon = datetime.getMonth()+1 + '-';
           let d = datetime.getDate();
           return y + mon + d;
       }
       return ''
    },
    fslxFormat(row, column){
      let key = row[column.property];
      if(key){
        return this.sflxDic[key];
      }
    },
      sfxsFormat(row, column){
      let key = row[column.property];
      if(key){
        return this.sfxsDic[key];
      }
    },
    prev(){
this.$router.go(-1)

}
  
  },
  watch: {
    // keyword: function(newData, oldData) {
    //   console.log("keyword newData:", newData); //newData就是orderData
    // }
  },
  created: function () {
    this.base_id = this.$route.query.base_id
    this.base_name = this.$route.query.base_name
    this.page = 1
    this.initRecords()
  },
}
</script>
<style scoped>
</style>