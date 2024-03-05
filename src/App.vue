
<script setup>
import { onMounted, ref, reactive } from 'vue';
import * as echarts from 'echarts';//引入

import Head from './views/head.vue'
import content from './views/content.vue'

const chart = ref();//创建dom引用


</script>

<template>

 <!-- 11 -->
 <!-- <div class="he">你好</div> -->


  <!-- <div ref="chart" style="width: 1080px;height: 1000px;"></div> -->

  
  <div class="module">
     <!-- 头部 -->
    <Head/>
    <!-- 内容 -->
    <content/>
  </div>


</template>

<style scoped>


</style>
