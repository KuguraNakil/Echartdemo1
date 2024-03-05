<template>
    <!-- 日历 -->
    <div class="calendar">
        <div class="calendar-left">
             <!-- 特殊边框 -->
             <div class="notice-border"></div>
            <div class="notice-bordertwo"></div>
            <div class="calen">

                <Calen />
            </div>
        </div>
        <div class="calendar-right">
             <!-- 特殊边框 -->
             <div class="notice-border"></div>
              <div class="notice-bordertwo"></div>
            <div class="left-img">
                <div class="red-img">

                    <img :src="chatimg" alt="" />


                </div>
                <div class="blue-img">

                    <img :src="chatimg" alt="" />


                </div>


            </div>
            <div class="right-text">
                <div class="text-content" v-for="(item, index) in contentdata" :key="index">
                    <div class="text-title">{{ item.time }}</div>
                    <div class="text">{{ item.detail }}</div>

                </div>



            </div>





        </div>




    </div>





    <!-- 图表 -->

    <!-- 图表数据 -->




</template>

<script setup>

import { onMounted, ref, reactive } from 'vue';
import * as echarts from 'echarts';//引入
import Calen from './calen.vue'
import chatimg from '../assets/tb2.png'


// const chart = ref();//创建dom引用
const value = ref(new Date())



let contentdata = [
    {
        "time": "2019-02-22",
        "detail": "下午14：00设计部在会议室技术培训，希望相关人员准时参加。",

    },
    {
        "time": "2019-02-19",
        "detail": "下午16：00运营部在会议室技术培训，希望相关人员准时参加。",
    },

]









onMounted(() => {







    // 响应式
    window.addEventListener("resize", () => {
        myChart.resize();
    })




})

</script>

<style lang="scss" scoped>
.calendar {
    width: 100%;
    height: 396px;
    border: 1px solid rgba(35, 39, 89, 1);
    border-radius: 10px;
    display: flex;

    .calendar-left {
        width: 60%;
        position: relative;

.notice-border {
position: absolute;
width: 20px;
height: 20px;
top: 0;
right: 0;
border-top: 3px solid #3B54D3;
border-right: 2px solid #3B54D3;
z-index: 5;
}
.notice-bordertwo{
position: absolute;
width: 20px;
height: 20px;
bottom: 0;
right: 0;
border-bottom: 3px solid #3B54D3;
border-right: 2px solid #3B54D3;
z-index: 5;
}

        // .calen {}
    }

    .calendar-right {
        display: flex;
        justify-content: space-between;
        align-items: center;
        position: relative;
        .notice-border {
        position: absolute;
        width: 20px;
        height: 20px;
        top: 0;
        left: 0;
        border-top: 3px solid #3B54D3;
        border-left: 2px solid #3B54D3;
        z-index: 5;
    }
    .notice-bordertwo{
        position: absolute;
        width: 20px;
        height: 20px;
        bottom: 0;
        left: 0;
        border-bottom: 3px solid #3B54D3;
        border-left: 2px solid #3B54D3;
        z-index: 5;
    }



        .left-img {
            margin-top: 10px;
            margin-left: 20px;




            .red-img {
                display: flex;
                justify-content: center;
                align-items: center;
                width: 40px;
                height: 40px;
                border-radius: 50%;
                background-color: rgba(241, 15, 106, 1);

                img {
                    // 居中
                    display: block;

                    width: 85%;
                }
            }

            .blue-img {
                margin-top: 90px;
                display: flex;
                justify-content: center;
                align-items: center;
                width: 40px;
                height: 40px;
                border-radius: 50%;
                background-color: #3B54D3;

                img {
                    // 居中
                    display: block;

                    width: 85%;
                }
            }


        }

        .right-text {
           

            .text-content {
              
                padding: 10px;
               

                .text-title {
                    padding-left: 15px;
                    font-size: 18px;
                    font-weight: 500;
                    letter-spacing: 0px;
                    line-height: 24.7px;
                    color: rgba(255, 255, 255, 1);
                   
                    vertical-align: top;
                }

                .text {
                    /** 文本1 */
                    padding: 15px;
                    font-size: 16px;
                    font-weight: 500;
                    letter-spacing: 0px;
                    line-height: 21.95px;
                    color: rgba(98, 99, 120, 1);
                    text-align: left;
                    vertical-align: top;
                    border-bottom:1px solid rgb(50, 54, 108);  
                    
                    


                }
            }
        }

        }



    }</style>