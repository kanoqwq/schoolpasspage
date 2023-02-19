<template>
    <div class="main">
        <div class="success">
            <svg t="1676805052052" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
                p-id="3918" width="150" height="150">
                <path
                    d="M512 32C246.4 32 32 249.6 32 512s217.6 480 480 480 480-217.6 480-480S774.4 32 512 32z m268.8 380.8L496 697.6c-25.6 25.6-60.8 25.6-83.2 0L243.2 528c-25.6-25.6-25.6-60.8 0-83.2s60.8-25.6 83.2 0l128 128 240-240c25.6-25.6 60.8-25.6 83.2 0 25.6 19.2 25.6 54.4 3.2 80z"
                    p-id="3919" fill="#22AD38"></path>
            </svg>
        </div>
        <div class="main-content">
            <p class="content">
                <strong class="title">学校：</strong>
                <span>{{ student.school }}</span>
            </p>
            <p class="content">
                <strong class="title">学院：</strong>
                <span>{{ student.college }}</span>
            </p>
            <p class="content">
                <strong class="title">专业：</strong>
                <span>{{ student.major }}</span>
            </p>
            <p class="content">
                <strong class="title">班级：</strong>
                <span>{{ student.class }}</span>
            </p>
            <p class="content">
                <strong class="title">姓名：</strong>
                <span>{{ student.name }}</span>

            </p>
            <p class="content">
                <strong class="title">学号：</strong>
                <span>{{ student.id }}</span>
            </p>
        </div>
        <div class="time">
            <p id="date" class="time-inner">
                {{ dateTime }}
            </p>
            <p id="time" class="time-inner">
                {{ time }}
            </p>
        </div>
    </div>
</template>

<script setup lang='ts'>
import { ref, reactive, onMounted } from 'vue'
import moment from 'moment'

let times = new Date();
const hours = times.getHours()
let dayStatus = ''
if (hours > 0 && hours <= 10) {
    dayStatus = '上午'
} else if (hours > 10 && hours <= 14) {
    dayStatus = '中午'
} else if (hours > 14 && hours <= 18) {
    dayStatus = '下午'
} else if (hours > 18 && hours <= 24) {
    dayStatus = '晚上'
}
const dateTime = ref(moment(new Date()).format('YYYY/M/DD'))
const time = ref(moment(new Date()).format(`${dayStatus}HH:mm:ss`))
setInterval(() => {
    time.value = moment(new Date()).format(`${dayStatus}HH:mm:ss`)
}, 100)
interface Student {
    school: string,
    college: string,
    major: string,
    class: string,
    name: string,
    id: string,
    [key: string]: string
}
const student: Student = reactive<Student>({
    school: '?',
    college: '?',
    major: '?',
    class: '?',
    name: "?",
    id: '?'
})
onMounted(() => {
    let queryArr: string[] = decodeURI(location.search).replace('?', '').split(':')
    if (queryArr.length < 6) {
        alert('请完整填写:\n格式?school:college:major:class:name:id')
    }
    let i = 0;
    for (let key in student) {
        console.log(key);
        student[key] = queryArr[i++]
    }

})

</script>

<style scoped>
.content {
    margin: 5px 0;
    text-align: left;
    color: #000;
}

.time {
    color: #000;
}

.time-inner {
    margin: -10px 0;
    font-size: 40px;
    font-weight: bold;
    background-image: -webkit-linear-gradient(bottom, #eee, #2a9b3b, #22AD38);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}
.main{
    margin-top: 100px;
}
</style>