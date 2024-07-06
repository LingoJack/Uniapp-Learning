<script setup>
import {ref} from "vue";

//可以显示的图片数组
const arr = ref([
  '../../static/demo1/pic1.png',
  '../../static/demo1/pic2.png',
  '../../static/demo1/pic3.webp',
  '../../static/demo1/pic4.jpg'
]);

//控制是否切换图片
const rolling = ref(true)

//显示的图片
const pic = ref(arr[0]);

//计数器，在达到图片数组的最大下标后回到0，达成重复播放
let count = 0;

setInterval(() => {
  if (rolling.value) {
    count++;
    if (count === arr.value.length) {
      count = 0;
    }
    pic.value = arr.value[count]
  }
}, 1000)

const isActive = ref(false)
const changeState = () => {
  rolling.value = !rolling.value;
  isActive.value = !isActive.value;
}

const size = ref(26)
const boxHeight = ref(100)
const bgcolor = ref()

const changeColor = () => {
  //随机生成一个数字，取六位作为rgb的十六进制表示
  bgcolor.value = '#' + String(Math.random()).substring(3, 9)
}

// 内置事件演示
//switch组件自带的返回值e，@change函数可以接收e作为参数

function onChange(e) {
  console.log('进行了切换')
  console.log(e)  //查看e的输出，可以看到detail.value为true或false，对应开关切换的状态
  console.log(e.detail.value)
}

</script>

<template>
  <view>
    <text>轮播图Demo（配合Vue3）</text>
  </view>
  <view>
    <image :src="pic" style="width: 100%"></image>
    <!--  字符串默认是true类型  -->
    <button type="primary" plain="true" style="color: #f0ad4e" @click="changeState">停止/开始</button>
  </view>
  <view class="box" :class="isActive?'active':''">
    v-bind绑定类名
    <!--  class="box active"后面的active会覆盖前面的box  -->
    <!--  多种写法都是ok的
      :class="{active:isActive}"
      :class="isActive?'active':''"
     -->
  </view>
  <view class="box" :style="{width: '300px',height:boxHeight +'px',fontSize:size+'px',background:bgcolor}">
    v-bind绑定style内联样式
    <!--  :style="{width: '300px',height:260 +'px',fontSize:26+'px'}  -->
  </view>
  <button @click="changeColor">随机一个颜色</button>
  <switch @change="onChange" checked="true"></switch>

</template>

<style lang="scss">
.box {
  width: 200px;
  height: 100px;
  color: #007aff;
  background-color: #f0ad4e;
}

.active {
  width: 250px;
  height: 150px;
  color: #4cd964;
  background-color: #3f536e;
}
</style>