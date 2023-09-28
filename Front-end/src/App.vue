<template>
  <div>
  <!-- <h1>{{message}}</h1> -->
  <!-- 把主Vue的代码屏蔽才会显示其它vue的代码 -->
  <!-- <element-view></element-view> -->
  <router-view></router-view>
  <!-- 员工管理 -->
<!-- <emp-view></emp-view> -->
<!-- 输入标签，引用其他的vue -->
  <!-- 在网页中显示 -->
  </div>
</template>

<script>
// import EmpView from './views/element/EmpView.vue'
// import ElementView from './views/element/ElementView.vue'
export default {
  components: {/*EmpView*/ /*ElementViewEmpView*/ },
  data() {
    return {
      message:"Hello Vue222"
    }
  },
  methods: {
    
  }
}
</script>


<style>

</style>

