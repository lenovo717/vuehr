<template>
    <div>
          <div class="permissManaTool">
              <el-input size="small" placeholder="请输入角色英文名" v-model="role.name">
                <template slot="prepend">ROLE_</template>
              </el-input>
              <el-input size="small" placeholder="请输入角色中文名" v-model="role.nameZh"></el-input>
             <el-button type="primary" size="small" icon="el-icon-plus" @click="doAddRole">添加角色</el-button>
          </div>
          <div class="permissManaMain">
              <el-collapse v-model="activeName" accordion @change="change">
                    <el-collapse-item :title="role.nameZh" :name="role.id" v-for="(role,index) in roles" :key="index">
                       <el-card class="box-card">
                            <div slot="header" class="clearfix">
                                <span>可删除资源</span>
                                <el-button style="float: right; padding: 3px 0" type="text" icon="el-icon-delete" @click="deleteRole(role)">操作按钮</el-button>
                            </div>
                            <div>
                                <el-tree
                                  show-checkbox
                                  node-key="id"
                                  ref="tree"     
                                 :key="index"
                                 :default-checked-keys="selectedMenus"
                                 :data="menus" :props="defaultProps" ></el-tree>
                                 <div style="display:flex;justify-content:flex-end">
                                     <el-button size="mini" @click="cancelUpdate()">取消修改</el-button>
                                     <el-button type="primary" size="mini" @click="doUpdate(role.id,index)">确认修改</el-button>
                                 </div>
                            </div>
                        </el-card>
                    </el-collapse-item>
                  
                  
                   
                </el-collapse>
          </div>
    </div>
  
</template>

<script>
export default {
    name:"PerMissMana",
    data(){
        return {
            role:{
                name:'',
                nameZh:''
            },
            activeName:'2',
            roles:[],
            menus:[],
            activeName:-1, //面板默认不展开
            selectedMenus:[],
            defaultProps: {
                        children: 'children',
                        label: 'name'
                        }
        }
    },methods:{
        deleteRole(role)
        {
             this.$confirm('即将删除, 是否继续?', '提示', {
                                        confirmButtonText: '确定',
                                        cancelButtonText: '取消',
                                        type: 'warning'
                                        }).then(() => {
                                            this.delRequest("/system/basic/permiss/role/"+role.id).then(resp=>{
                                                if(resp)
                                                this.initRole()
                                            })
                                        
                                        }).catch(() => {
                                        this.$message({
                                            type: 'info',
                                            message: '已取消删除'
                                        });          
                                        });
        },
        doAddRole()
        {
           if(this.role.name && this.role.nameZh)
           {
                this.postRequest("/system/basic/permiss/role/",this.role).then(resp=>{
                 if(resp){
                    this.role=[]
                    this.initRole()
                 }
             })
           }else
              this.$message.error("数据不能为空!")

            
             
        },
        initRole()
        {
             this.getRequest("/system/basic/permiss/").then(resp=>{
                 if(resp){
                     this.roles = resp
                 }
             })
        },
        initSelectedMenus(rid)
        {
             this.getRequest("/system/basic/permiss/mid/"+rid).then(resp=>{
                 if(resp){
                     this.selectedMenus = resp
                 }
             })
        },
        change(name)
        {
            console.log(name)
            //只有展开面板才调用
              if(name)
              {
                 this.initMenus()
                 this.initSelectedMenus(name)
              }
        },
        initMenus()
        {
                this.getRequest("/system/basic/permiss/menus/").then(resp=>{
                                if(resp){
                                    this.menus = resp
                                } 
                            })
        },
        doUpdate(rid,index)
        {

             console.log(rid)
             let tree = this.$refs.tree[index]
             //tree自带方法，获取选中的key true表示只返回叶子节点
             let selectKeys = tree.getCheckedKeys(true)
             console.log(selectKeys)
             let url = '/system/basic/permiss/?rid='+rid;
             selectKeys.forEach(element => {
                 url +='&mids='+element
             });

             this.putRequest(url).then(resp=>{
                 if(resp){
                      //this.initRole()
                      this.activeName = -1 //面板收缩
                 }
             })
        },
        cancelUpdate()
        {
            this.activeName = -1
        }

    },mounted(){
        this.initRole()
    }
}
</script>

<style >
    .permissManaTool {
        display: flex; /* 水平排列*/
    }
   .permissManaTool .el-input{
       width:300px;
       margin-right: 6px;
   }
   .permissManaMain {
       margin-top:10px;
       width:600px;
   }
</style>>