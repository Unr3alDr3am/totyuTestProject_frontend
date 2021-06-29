<template>
  <div>
    <div style="margin-bottom: 20px;">
      <el-row>
        <el-col :span="20" style="padding-left: 20px;">
          <el-row>
            <el-col :span="20" style="padding-left: 20px;text-align: left">
              <label for="studentname"></label>
              <el-input id="studentname"
                        placeholder="可以通过学生姓名搜索学生..."
                        prefix-icon="el-icon-search"
                        v-model="studentname" style="width: 400px" size="small"
              ></el-input>
            </el-col>
            <el-col :span="4">
              <el-button type="primary" icon="el-icon-search" size="small" @click="searchStudent">搜索</el-button>
            </el-col>
          </el-row>
        </el-col>
        <el-col :span="4">
          <el-button type="primary" icon="el-icon-circle-plus" size="small">添加学生</el-button>
        </el-col>
      </el-row>
    </div>
    <div>
      <el-table
          :data="studentList"
          size="mini"
          stripe
          style="width: 100%">
        <el-table-column  prop="name"   align="center" fixed label="名称" width="150"> </el-table-column>
        <el-table-column prop="age" align="left" fixed  label="年龄"   width="100"> </el-table-column>
        <el-table-column prop="gender" align="left" fixed  label="性别"   width="100"> </el-table-column>
        <el-table-column label="" align="right">
          <template slot-scope="scope">
              <el-button
                size="mini"  class="el-icon-edit" type="primary"
                @click="handleEdit(scope.$index, scope.row)">修改
            </el-button>

            <el-button
                size="mini"
                class="el-icon-delete" type="danger"
                @click="handleDelete(scope.$index, scope.row)">删除
            </el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
  <!--修改学生信息表单 -->
    <el-form :model="userForm" :rules="rules" ref="editUserForm" style="margin: 0px;padding: 0px;">
      <div>
        <el-dialog
            :title="dialogTitle"
            style="padding: 0px;text-align: center"
            :close-on-click-modal="false"
            :visible.sync="dialogVisible"
            width="300px">
          <el-row>
            <el-col>
              <el-form-item label="姓名:" prop="name">
                <el-input  v-model="studentForm.name" size="mini" style="width: 150px" placeholder="请输入姓名"></el-input>
              </el-form-item>
            </el-col>
          </el-row>
            <el-row>
            <el-col>
              <el-form-item label="年龄:" prop="age">
                <el-input  v-model="studentForm.age" size="mini" style="width: 150px"
                           placeholder="请输入用户名"></el-input>
              </el-form-item>
            </el-col>
          </el-row>
          <el-row>
            <el-col>
              <el-form-item label="性别:" prop="gender">
                <el-select v-model="studentForm.gender" placeholder="请选择" style="width:150px;" size="mini">
                  <el-option
                      v-for="item in genderOptions"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value">
                  </el-option>
                </el-select>
              </el-form-item>
            </el-col>
          </el-row>
          <span slot="footer" class="dialog-footer">
        <el-button size="mini" @click="resetUser">取 消</el-button>
        <el-button size="mini" type="primary" @click="saveUser('addUserForm',userForm.id)">确 定</el-button>
      </span>
        </el-dialog>
      </div>
    </el-form>
  </div>

</template>

<script>
export default {
  name:"studentlist",
  mounted: function () {
    //加载后台数据
    this.loadStudentsList();
  },
  data(){
    return{
      studentList:[
        {
          name:"test1",
          age:18,
          gender:"男"
        }
      ],
      studentForm:{
        name:"",
        age:"",
        gender:""
      },
      genderOptions:[
        {
          value:0,
          label:'男'
        },
        {
          value: 1,
          label: '女'
        }
      ],
      studentname:"",
      dialogTitle:"",
      dialogVisible:true
    }
  },
  methods:{
    loadStudentsList(){
      //获取后台数据
    },
    searchStudent(){
      //搜索学生信息

    },

  }
}
</script>

<style>

</style>