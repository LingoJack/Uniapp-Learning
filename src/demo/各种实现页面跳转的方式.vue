<script setup>
function jumpToUserByNavigateTo(){
  uni.navigateTo({
    url:'../user/user'
  })
}

function goUserbyUniSwitchTab(){
  uni.switchTab({
    url:'../user/user'
  })
}

function goUserbyUniReLaunch(){
  uni.reLaunch({
    url:'../user/user'
  })
}

function goBack(){
  //getCurrentPages()可以获得当前页面栈的实例，第一个元素为首页，最后一个元素为当前页面
  console.log(getCurrentPages())

  uni.navigateBack()
}


</script>

<template>
  <view class="layout">
    页面跳转演示（代码）
    <!--  url的跳转地址不能为TabBar地址，下面这样是无法跳转的  -->
    <navigator url="pages/user/user">跳转User(错误演示)</navigator>
    <text>---------</text>
    <navigator open-type="switchTab" url="../user/user">switchTab跳转User</navigator>
    <text>---------</text>
    <navigator open-type="reLaunch" url="../user/user">reLaunch跳转User</navigator>
    <text>---------</text>
    <!--
      这种方式也不能跳转到TabPage，
      想跳转到TabPage得用uni.switchTab或者
    -->
    <button @click="jumpToUserByNavigateTo">NavigateTo跳转User（错误演示）</button>
    <button @click="goUserbyUniSwitchTab">uni.switchTab跳转User</button>
    <button @click="goUserbyUniReLaunch">uni.reLaunch跳转User</button>
    <text>---------</text>
    <!--  uni.navigateBack返回上一级或者多级页面  -->
    <button @click="goBack">uni.navigateBack跳回上一级或者多级页面</button>
    <text>---------</text>
    <text>---------</text>
    <text>---------</text>
  </view>
</template>

<style lang="scss">

</style>