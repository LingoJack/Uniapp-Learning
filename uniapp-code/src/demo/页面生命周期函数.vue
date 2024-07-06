<script setup>
import {ref} from "vue";
import {onLoad} from "@dcloudio/uni-app";

const name=ref('LingoJack')
onLoad((event)=>{
  name.value='WenJunjie'
  console.log('onLoad页面生命周期函数调用了')
  console.log(event)
})

</script>

<template>
  <!--
    页面生命周期函数。onLoad使用前必须导入：import {onLoad} from "@dcloudio/uni-app";
    使用方式和组件声明周期函数onMounted差不多。
    但是onLoad可以接收上一个页面传递过来的event作为onLoad的参数
    页面跳转之间可以这么传递数据：
    <navigator url="../user/user?name=Lingo&age=19">跳转</navigator>
    在user/user页面中的onLoad函数以(event)作为参数即可拿到name:Lingo,age:19
  -->
  <view class="layout">
    <text>姓名：{{name}}</text>
    <navigator url="../user/user?name=Lingo&age=19">跳转</navigator>
  </view>


</template>

<style lang="scss" scoped>

</style>