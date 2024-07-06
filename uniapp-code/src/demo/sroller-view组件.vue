<script setup>

</script>

<template>
  <view class="layout">
    <!--  hover-class是用户手指按在组件上显示的样式，即，点击态  -->
    <!--  view组件的文字内容是无法选中的  -->
    <view class="box1" hover-class="hoverBox1">view组件</view>
    <view class="box2">I am LingoJack</view>
  </view>

  <text selectable="true">可以选中text组件</text>

  <!-- 设置scroll-y属性可以y轴滚动 -->
  <scroll-view class="scrollView" scroll-y="true">
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
    <view class="box2">I am LingoJack</view>
  </scroll-view>

  <navigator url="/pages/user/user">
    跳转到User
  </navigator>

</template>

<style lang="scss">
//  嵌套的样式必须使用scss，因为嵌套路由是原生的css所不支持的
.layout {
  .box1 {
    color: greenyellow;
    width: 200px;
    height: 100px;
    background-color: #f0ad4e;
  }

  .box2 {
    color: #007aff;
    width: 200px;
    height: 100px;
    background-color: grey;
  }

  .hoverBox1 {
    background-color: #dd524d;
  }
}

.scrollView {
  width: 80%;
  height: 20%;
  border: 1px solid red;
}
</style>