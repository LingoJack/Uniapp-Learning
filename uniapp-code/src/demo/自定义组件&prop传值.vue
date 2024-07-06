<script setup>
import UserInfo from "../../components/UserInfo.vue";
</script>

<template>
  <!-- 演示自定义组件的使用方式，以及prop属性-->
  <!-- 组件必须放在src/components这个目录下 -->
  <!--
     还可以把username和avatar封装成一个对象传递过去，obj是一个对象，所以这里应该是v-bind:
    <user-info :obj="{"a":1,"b":2}"></user-info>
   -->
  <!--  -->
  <user-info username="LingoJack" avatar="../static/demo1/pic1.png"></user-info>

</template>

<style lang="scss" scoped>

</style>