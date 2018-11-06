<template>
    <div>
           <div style="position: absolute;top:0;left:0;bottom:0px;right:0px; background-color:#333;opacity: 0.5;z-index: 1;"></div>
        <div style="position: absolute;width: 100vw;z-index: 2;">
        <el-container>
            <el-main style="margin-top:2rem;">
                <el-row >
                    <el-col style="background-color:#fff;" :span="12" :offset="6">
                        <div >
                            <div class="changstyle1" style="margin-top:0rem;" >
                                  <div style="width:18px;height:18px;position:absolute;top:0rem;right:0.5rem;z-index:111">
                                          <el-button style="border:0px solid #fff;padding:0rem;" @click="cancel3">
                                                <img :src="cancel" alt="取消" width='25px'>
                                          </el-button>
                                </div>
                                <el-row>
                                    <el-col :span="24"><div class="changstyle2">添加</div></el-col>
                                </el-row>
                               <el-form :model="ruleForm2" status-icon  ref="ruleForm2" label-width="6rem" >
                                    <el-form-item label="站点名" prop="s_site_name">
                                        <el-input placeholder="请输入站点名" v-model="ruleForm2.s_site_name"></el-input>
                                    </el-form-item>
                                    <el-form-item style="line-height:-1rem;" label="取样点名" prop="s_name">
                                        <el-input placeholder="请输入取样点名" v-model="ruleForm2.s_name"></el-input>
                                    </el-form-item>
                                    <el-form-item style="line-height: 1rem!important;" label="pid位" prop="s_pid">
                                        <el-input placeholder="请输入pid位" v-model="ruleForm2.s_pid" ></el-input>
                                    </el-form-item>
                                    <el-form-item label="取样点温度" prop="s_temperature">
                                        <el-input placeholder="请输入取样点温度" v-model="ruleForm2.s_temperature" >
                                               <template slot="append">℃</template>
                                        </el-input>
                                    </el-form-item>
                                    <el-form-item label="压力" prop="s_pressure">
                                        <el-input   placeholder="请输入压力" v-model.number="ruleForm2.s_pressure">
                                              <template slot="append">MPa</template>
                                        </el-input>
                                    </el-form-item>
                                   <el-form-item label="流量" prop="s_flow">
                                        <el-input placeholder="请输入流量" v-model="ruleForm2.s_flow">
                                            <template slot="append">m³/h</template>
                                        </el-input>
                                    </el-form-item>
                                    <el-form-item label="含水率" prop="s_water">
                                        <el-input placeholder="请输入含水率" v-model="ruleForm2.s_water">
                                             <template slot="append">%</template>
                                        </el-input>
                                    </el-form-item>
                                     <el-form-item label="气液比" prop="s_gas" >
                                        <el-input placeholder="请输入气液比" v-model="ruleForm2.s_gas">
                                             <template slot="append" >scf/stb</template>
                                        </el-input>
                                    </el-form-item>
                                      <el-form-item label="化学药剂" prop="s_medicament" >
                                        <el-input placeholder="请输入化学药剂" v-model="ruleForm2.s_medicament"></el-input>
                                    </el-form-item>
                                      <el-form-item label="注射量" prop="s_injectivity" >
                                        <el-input placeholder="请输入注射量" v-model="ruleForm2.s_injectivity"></el-input>
                                    </el-form-item>
                                      <el-form-item label="二氧化碳含量" prop="s_carbon" >
                                        <el-input placeholder="请输入二氧化碳含量" v-model="ruleForm2.s_carbon"></el-input>
                                    </el-form-item>
                                      <el-form-item label="硫化氢" prop="s_sulfide" >
                                        <el-input placeholder="请输入硫化氢" v-model="ruleForm2.s_sulfide"></el-input>
                                    </el-form-item>
                                      <el-form-item label="图片" prop="s_image" >
                                        <el-input placeholder="请输入图片" v-model="ruleForm2.s_image"></el-input>
                                    </el-form-item>
                                        <el-button type="primary" @click="submitForm('ruleForm2')">添加</el-button>
                                </el-form>
                            </div>
                        </div>
                    </el-col>
                </el-row>
            </el-main>
        </el-container>
        </div>
    </div>
</template>
<script>
import ajax from '../common/ajax';
import cancel from '../../static/cancel.png';
export default {
    name:'register1',
    data(){
    //      var checknumber = (rule, value, callback) => {
    //     if (!value) {
    //       return callback(new Error('电话不能为空'));
    //     }
    //     setTimeout(() => {
    //         if (!Number.isInteger(value)) {
    //             callback(new Error('请输入数字值'));
    //         }else if(value < 10000000000){
    //                 callback(new Error('请输入11位数字的电话号码'));
    //         }else  if(value > 100000000000){
    //             callback(new Error('请输入11位数字的电话号码'));
    //         }else{
    //             callback();
    //         }
    //         }, 1000);
    //     };
    //     var checkLevel = (rule, value, callback) => {
    //         if (!value) {
    //         return callback(new Error('等级不能为空'));
    //         }else if(value == '操作管理员' || value == '站点管理员' || value == '公司管理员' || value == '超级管理员' ) {
    //             callback();
    //         }else if (value != '操作管理员' || value != '站点管理员' || value != '公司管理员' || value != '超级管理员' ) {
    //             callback(new Error('请输入正确的内容'));
    //         }
    //     };
    //      var validatePass = (rule, value, callback) => {
    //         if (value === '') {
    //         callback(new Error('请输入密码'));
    //         } else {
    //         if (this.ruleForm2.checkPass !== '') {
    //             this.$refs.ruleForm2.validateField('checkPass');
    //         }
    //         callback();
    //         }
    //     };

    //     var validateaffiliation = (rule, value, callback) => {
    //         if (value === '') {
    //         callback(new Error('请输入用户归属地'));
    //         } else {
    //         callback();
    //         }
    //     };
    //      var validateremark = (rule, value, callback) => {
    //         if (value === '') {
    //         callback(new Error('请输入用户备注'));
    //         } else {
    //         callback();
    //         }
    //     };
    //   var validatePass2 = (rule, value, callback) => {
    //     if (value === '') {
    //       callback(new Error('请再次输入密码'));
    //     } else if (value !== this.ruleForm2.password) {
    //       callback(new Error('两次输入密码不一致!'));
    //     } else {
    //       callback();
    //     }
    //   };
// 站点获取
// http://jenk.gd.cn:8080/FB/site/select


         return{
             cancel,
            ruleForm2: {
                uid:window.localStorage.getItem('uid'),
                s_id:"",
                s_name:"",
                s_pid:"",
                s_temperature:"",
                s_pressure:"",
                s_water:"",
                s_gas:"",
                s_medicament:"",
                s_injectivity:"",
                s_carbon: "",
                s_sulfide:"",
                s_image:"",
                s_flow:"",
                s_site_name:"",
            }
        }
    },
     methods: {
         cancel3(){
                this.$emit('closeparent300');
         },
      submitForm(formName) {
           this.$confirm('是否确认添加管理员信息', '确认信息', {
                distinguishCancelAndClose: true,
                confirmButtonText: '确认添加',
                cancelButtonText: '继续添加'
            })
            .then(() => {
                this.$message({
                type: 'info',
                message: '请等待...',
                });
             this.$refs[formName].validate((valid) => {
                if (valid) {
                    var url = "http://jenk.gd.cn:8080/FB/sampling/add";
                    var _this = this;
                    var obj = {};
                    obj.s_name = _this.ruleForm2.s_name;
                    obj.s_pid = _this.ruleForm2.s_pid;
                    obj.uid = _this.ruleForm2.uid;
                    obj.s_temperature = _this.ruleForm2.s_temperature;
                    obj.s_pressure = _this.ruleForm2.s_pressure;
                    obj.s_flow = _this.ruleForm2.s_flow; 
                    obj.s_sulfide = _this.ruleForm2.s_sulfide; 
                    obj.s_carbon = _this.ruleForm2.s_carbon; 
                    obj.s_injectivity = _this.ruleForm2.s_injectivity; 
                    obj.s_medicament = _this.ruleForm2.s_medicament; 
                    obj.s_gas = _this.ruleForm2.s_gas;  
                    obj.s_water = _this.ruleForm2.s_water;  
                    obj.s_image = _this.ruleForm2.s_image;  
                    obj.s_site_name = _this.ruleForm2.s_site_name;  
                    ajax.inAjaxpost(url,obj,(data)=>{
                        if(data.code == 108){
                            alert('失败');
                            return false;
                        }
                        if(data.code == 200){
                            alert('添加成功');
                            _this.ruleForm2.s_name = '';
                            _this.ruleForm2.s_pid = '';
                            _this.ruleForm2.s_temperature = '';
                            _this.ruleForm2.s_pressure = ''; 
                            _this.ruleForm2.s_flow= '';
                            _this.ruleForm2.s_image= '';
                            _this.ruleForm2.s_sulfide= '';
                            _this.ruleForm2.s_carbon= '';
                            _this.ruleForm2.s_injectivity= '';
                            _this.ruleForm2.s_medicament= '';
                            _this.ruleForm2.s_gas= '';
                            _this.ruleForm2.s_water= '';
                            _this.ruleForm2.s_site_name= '';
                            this.$emit('closeparent100s');
                        }
                    })
                } 
                })
            })
            .catch(action => {
                this.$message({
                type: 'info',
                message: action === 'cancel'
                    ? '继续添加'
                    : '停留在当前页面'
                })
            });
       
      }
     }
}
</script>
<style scoped>
.changstyle1{
    position: relative;
    box-sizing: border-box;
     border: 2px solid #000;
}

.changstyle2{
    font-size: 1.6rem;
    padding: 0.8rem;
    color:rgb(10, 10, 10);
    font-weight: bolder;
}
.el-button--primary{
    font-size: 1.2rem;
    width:80%;
    margin-bottom: 1rem;
}
.el-form{
    width:88%;
    margin:0 auto;
}
.el-form-item {
    margin-bottom: 0px !important;
}
</style>

