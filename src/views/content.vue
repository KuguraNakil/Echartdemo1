<script setup>

import { onMounted, ref, reactive } from 'vue';
import * as echarts from 'echarts';//引入
// 左上
import Attendance from '../components/attendance.vue'
// 左下
import RoomUse from '../components/roomuse.vue'
// 右边办公
import Inform from '../components/inform.vue'
// 右边饼图1
import Chart from '../components/chart.vue'
// 右边饼图2
import ChartTwo from '../components/charttwo.vue'
// 中上日历
import Calendar from '../components/calendar.vue'
// 中下公告1
import NoticeOne from '../components/noticeone.vue'
// 中下公告2
import NoticeTwo from '../components/noticetwo.vue'



const chart = ref();//创建dom引用

onMounted(() => {


    // 绘制图表


})

</script>

<template>
    <!-- 内容 -->
    <div class="content">



        <div class="content-left">
            <Attendance />
            <!-- 考勤 -->

            <!-- 会议室使用情况 -->
            <RoomUse />

        </div>

        <div class="content-mid">

            <!-- 日历 -->
          
            <Calendar />

            <!-- 饼图1 -->
            <!-- 在审核 -->
         
            <NoticeOne/>
            <!-- 已审核 -->
            <NoticeTwo/>
            
        </div>




        <div class="content-right">
            <!-- 通知办公 -->
            <Inform />
            <!-- 饼图1 -->
            <!-- 流程使用率 -->
            <Chart />
            <!-- 饼图2 -->
            <ChartTwo />
        </div>

    </div>
</template>



<style lang="scss" scoped>
.content {
    display: flex;
    justify-content: space-between;





    // 左边部分
    .content-left {
        max-width: 460px;
        /* 设置左侧部分的最大宽度 */
        margin-bottom: 20px;
        /* 添加底部间距 */
        width: 100%;
        margin-left: 1%;





    }

    // 中间部分
    .content-mid {
        width: 100%;
        // border: 1px solid #ccc;
        max-width: 925px;
        /* 设置中间部分的最大宽度 */
        margin: 0 20px;

        /* 添加左右间距 */
      

       

    }

    .content-right {
        width: 100%;
        max-width: 450px;
        /* 设置右侧部分的最大宽度 */
        // border: 1px solid #ccc;
        margin-bottom: 20px;
        /* 添加底部间距 */
        margin-right: 1%;
    }
}
</style>