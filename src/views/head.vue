<template>
    <div class="head">
        <div class="title">
            网络科技办公自动化监控系统
        </div>
        <div class="day">
            <div class="date">
                {{ currentDate }}
            </div>
            <div class="week">
                {{ currentDay }}
            </div>
            <div class="time">
                {{ currentTime }}
            </div>
        </div>
        <!-- 绘制边框 -->
        <div>
            <canvas class="draw" ref="line"></canvas>
        </div>
    </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
    setup() {
        const currentDate = ref('');
        const currentDay = ref('');
        const currentTime = ref('');

        const getCurrentTime = () => {
            const now = new Date();
            const year = now.getFullYear();
            const month = now.getMonth() + 1;
            const day = now.getDate();

            currentDate.value = `${year}-${month}-${day < 10 ? '0' + day : day}`;
            currentDay.value = getDayOfWeek(now.getDay());
            currentTime.value = now.toLocaleTimeString();
        };

        const getDayOfWeek = (day) => {
            const days = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
            return days[day];
        };

        onMounted(() => {
            getCurrentTime();
            setInterval(() => {
                getCurrentTime();
            }, 1000); // 更新时间每秒
        });

        return {
            currentDate,
            currentDay,
            currentTime
        };
    }
};
</script>

<style scoped lang="scss">
// 标题
.head {
    width: 100%;
    height: 169px;
    opacity: 1;
    // border: 1px solid rgba(35, 39, 89, 1);
    position: relative;
    border: 1px solid rgba(35, 39, 89, 1);




    .title {
        margin-top: 35px;
        padding-bottom: 10px;
        opacity: 1;
        /** 文本1 */
        font-size: 36px;
        font-weight: 500;
        letter-spacing: 1.8px;
        line-height: 49.39px;
        color: rgba(255, 255, 255, 1);
        text-align: center;
        // border-bottom: 1px solid rgba(35, 39, 89, 1);
        // vertical-align: top;
    }



    .day {
        display: flex;
        opacity: 1;

        /** 文本1 */
        font-size: 18px;
        font-weight: 500px;
        letter-spacing: 0.9px;
        line-height: 24.7px;
        color: rgba(127, 144, 171, 1);
        text-align: center;
        vertical-align: top;
        align-items: center;
        justify-content: center;

        .date {
            margin: 5px 10px 10px 10px;
        }

        .week {
            margin: 5px 10px 10px 10px;
        }

        .time {
            margin: 5px 10px 10px 10px;
        }


    }

    .draw {
        width: 100%;
        height: 35px;
        // border: 1px white solid;

    }

    //  .ablock {
    //         width: 30%;
    //         // height: 60px;
    //         border: 1px solid rgba(35, 39, 89, 1);
    //         position: absolute;
    //         left: 0;
    //         top: 80%;

    //         // 左下角居中
    //         transform: translate(0, 50%);


    //     }
}

//sss
.demo {
    width: 500px;
    height: 500px;
    border: 3px solid #253365;
    margin: 15px auto;
}

.demo .block {
    background: #253365;
    width: 100px;
    height: 10px;
    position: relative;
    margin: 0 auto;
}

.demo .block:before,
.demo .block:after {
    content: '';
    width: 0;
    height: 0;
    border: 10px solid transparent;
    border-top-color: #253365;
    display: block;
    position: absolute;
    left: 0;
    transform: translate(-50%);
}

.demo .block:after {
    left: auto;
    right: 0;
    transform: translate(50%);
}

body {
    width: 100vw;
    height: 100vh;
    background: #060d2a;
    display: flex;
}
</style>