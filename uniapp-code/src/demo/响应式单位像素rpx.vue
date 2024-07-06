<script setup>

</script>

<template>
  <view class="box"></view>
</template>

<style lang="scss" scoped>
.box{
  //这种固定像素的写法并不好，因为不同的机型的屏幕大小不同，会造成不同机型页面显示的不一致
  //width: 200px;
  //height: 200px;
  height: 200px;    //高度height不用响应式单位
  background-color: #4cd964;
  //要使用响应式单位像素，就能让渲染的大小根据不同机型的屏幕大小来改变
  //或者说，百分比像素，比如：（下面三种写法是等价的）
  //百分比写法
  width: 50%;

  //vw，即视觉宽度view width
  //width: 50vw;

  //以750rpx为基准，width:375rpx等价于width:375/750，即width:50%
  //width: 375rpx;
}

</style>