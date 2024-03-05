<template>
    <div class="inform">
        <div class="inform-title">
            通知办公
        </div>
        <div class="inform-content" v-for="(item, index) in informcontent" :key="index">
            <div class="content-top">
                <div class="content-title">
                    {{ item.title }}
                </div>
                <!-- 关闭按钮 -->
                <div class="content-close">
                    <el-icon :size="15" color="red">
                        <Close />
                    </el-icon>

                </div>

            </div>

            <!-- 分割线 -->
            <div class="content-line"></div>
            <!-- 内容 -->
            <div class="content">

                <div class="content-text">
                {{ item.detail }}
            </div>

            <div class="content-bottom">
                <span class="time">
                    {{ item.time }}
                </span>
               <span class="name">
                {{ item.name }}
               </span>
              
            </div>
            </div>

         


















        </div>




    </div>
</template>

<script setup>

import { onMounted, ref, reactive } from 'vue';
import * as echarts from 'echarts';//引入
import { Close } from '@element-plus/icons-vue'

let informcontent = {
    "data": {
        "detail": "早上9：00在大会议室召开项目总结会，希望公司全体人员准时参加。",
        "title": "会议通知",
        "time": "2019-2-26 10：00",
        "name": "张三",
    }

}
 // 响应式
 window.addEventListener("resize",  ()=> {
        myChart.resize();
    })



</script>

<style lang="scss" scoped>
.inform {
    left: 1438px;
    top: 109px;
    width: 100%;
    height: 302px;
    opacity: 1;
    border: 1px solid rgba(35, 39, 89, 1);
    border-radius: 10px;
    margin-bottom: 10px;
    

    .inform-title {

        font-size: 20px;
        font-weight: 500;
        letter-spacing: 0px;
        line-height: 27.44px;
        color: rgba(205, 214, 229, 1);
        margin: 20px;
        vertical-align: top;
    }

    .inform-content {

        width: 85%;
        height: 60%;
        opacity: 1;
        border: 1px solid rgba(35, 39, 89, 1);
        border-radius: 10px;
        margin: 20px auto;

        .content-top {
            display: flex;
            justify-content: space-between;
            margin: 20px;

            .content-title {

                font-size: 18px;
                font-weight: 500;
                letter-spacing: 0px;
                line-height: 24.7px;
                color: rgba(255, 255, 255, 1);
                margin-left:20px; 
                vertical-align: top;
            }
        }


        .content-line {
            width: 90%;
            height: 1px;
            background-color: rgba(35, 39, 89, 1);
            margin: 0 auto;
        }

        .content{

            margin:20px;

        .content-text {


            /** 文本1 */
            font-size: 16px;
            font-weight: 500;
            letter-spacing: 0px;
            line-height: 21.95px;
            color: rgba(98, 99, 120, 1);
            text-align: left;
            vertical-align: top;
            text-indent: 10%;
            
        }
        .content-bottom{
            font-size: 16px;
            font-weight: 500;
            letter-spacing: 0px;
            line-height: 21.95px;
            color: rgba(98, 99, 120, 1);
            text-align: left;
            vertical-align: top;
            margin-top: 5px ;

        }

        .time{
            margin: 5px;

        }

        .name{
            margin: 5px;
        }


    }

    }



}
</style>