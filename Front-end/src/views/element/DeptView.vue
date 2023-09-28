<template>
  <div>
    <el-container style="height: 700px; border: 1px solid #eee">
      <el-header style="font-size:40px;background-color: rgb(238, 241, 246)"
        >tlias智能学习系统</el-header
      >
      <el-container>
        <el-aside width="230px" style="border: 1px solid #eee">
          <!-- 有滚动条是因为宽度小，宽度调大即可 -->
          <el-menu :default-openeds="['1', '3']">
            <el-submenu index="1">
              <template slot="title"
                ><i class="el-icon-message"></i>系统信息管理</template
              >
              <el-menu-item-group>
                <template slot="title">分组一</template>
                <el-menu-item index="1-1">
                  <router-link to="/dept">部门管理</router-link>
                </el-menu-item>
                <el-menu-item index="1-2">
                     <router-link to="/emp">员工管理</router-link>
                </el-menu-item>
            </el-menu-item-group>
            </el-submenu>
          </el-menu></el-aside
        >

            <!-- 表单 -->
        <!-- 绑定了模型，就必须要建立，否则页面就会什么都不显示 -->
         <el-main>
                 <!-- 主体容器不需要多开！一个就够了，你之所以分开了两块区域
          就是因为你多开了一个主体容器！ -->
          <!-- 你把表单表格用main容器框在一起就没问题了 -->
          
          
        <el-form :inline="true" :model="searchForm" class="demo-form-inline">
          <el-form-item label="姓名">
            <el-input v-model="searchForm.name" placeholder="姓名"></el-input>
          </el-form-item>

          <el-form-item label="性别">
            <el-select v-model="searchForm.gender" placeholder="性别">
              <el-option label="男" value="1"></el-option>
              <el-option label="女" value="2"></el-option>
            </el-select>
          </el-form-item>

          <el-form-item label="入职日期">
            <!-- 日期选择器 -->
            <span class="demonstration">默认</span>
            <el-date-picker
              v-model="searchForm.entrydate"
              type="daterange"
              range-separator="至"
              start-placeholder="开始日期"
              end-placeholder="结束日期"
            >
            </el-date-picker>
          </el-form-item>

          <el-form-item>
            <el-button type="primary" @click="onSubmit">查询</el-button>
            <!-- 建立onSubmit方法，要加入方法 -->
 
          </el-form-item>
        </el-form> 

  
        <!-- 表格 -->

          <el-table :data="tableData" border>
            <!-- 指向数组，所以自己要创建一个数组 -->
            <el-table-column prop="date" label="日期" width="140">
            </el-table-column>
            <el-table-column prop="name" label="姓名" width="120">
            </el-table-column>
              <el-table-column label="图像" width="180">
                        <template slot-scope="scope">
             <img :src="scope.row.image" width="100px" height="70px">
             <!-- 冒号是写在src前，不是img前 -->
             <!-- 加冒号是标记动态绑定的操作 -->
        <!-- 实行动态更新图片的操作
  -->
              </template>
            </el-table-column>
            <el-table-column  label="地址">
              <!-- 有了插槽后就不需要prop了 -->
              <template slot-scope="scope">
                {{scope.row.gender==1?'男':'女'}}
 
              </template>

            </el-table-column> 
            </el-table
        >
        
        <br>
         <!-- pagination 分页 -->
    <el-pagination
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      background
      layout="sizes,prev, pager, next,jumper,total"
      :total="1000"
    >
    <!-- 两个编辑是在标签中添加！ -->
    </el-pagination>
        
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return {
      tableData: [],
      searchForm: {
        name: "",
        gender: "",
        entrydate:[]
      },
    };
  },
  methods: {
    onsubmit() {
      alert("查询数据");
    },
     handleSizeChange(val) {
      alert("每页记录数变化"+val);
    },
    handleCurrentChange(val) {
      alert("页码发生变化"+val);
    },
  },
  mounted () {
    //发送异步请求，获取数据
    axios.get("xxx存有数据的网址").then((result) => {
      this.tableData=result.data.data;
    });
  }
  };
</script>

<style>
</style>