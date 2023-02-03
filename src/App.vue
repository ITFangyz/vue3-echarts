<template>
  <router-view/>
</template>

<script>
  import {provide} from 'vue'
  import  * as echarts from 'echarts'  //引入echarts所有内容
  import axios from 'axios'

//设置基准路径
axios.defaults.baseURL = "http://39.108.15.20:8088/"

 export default {
  setup(){
    provide("echarts", echarts)
    provide("axios", axios)
  }
 }
</script>

<style lang="less">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  background: url("~@/assets/bg.jpg") top center no-repeat;
  background-size: 100% 100% 
}

</style>
