<script setup>
/*uni-api交互反馈showToast的用法*/
uni.showToast({
  title:"欢迎回来",
  // icon有几种预制的类型，常用的有success,fail,none，默认是success
  //icon:"success",
  //自定义图片路径
  image:"../../static/icons/success.png",
  //设置在弹窗出现时候不能点击该页面除弹窗外的内容
  //mask:true,
  //延迟时间：默认为1500ms
  //duration:500,
  duration:3000,
  //成功的回调函数,fail是失败的回调，completed是成功和失败都会调用的回调
  success:(e)=>{
    console.log(e);
  }
})

//学习到这里的时候已经配置了自动导入的插件，所以不用再手动导入ref
function hide(){
  //隐藏弹窗
  uni.hideToast()
}

function show(){
  uni.showToast({
    //显示弹窗
    image:"../../static/icons/success.png"
  })
}


</script>

<template>
  <view class="content">
    <!-- 这样是跳转不了的，因为url属性只能控制跳转到非tabBar页面:
        <navigator url="../user/user">尝试用navigator的url属性跳转tabBar页面</navigator>
    -->
    <!-- 除非设置open-type属性为switchTab或者reLaunch  -->
    <navigator open-type="reLaunch" url="/pages/user/user">reLaunch跳转到User页面</navigator>
    <navigator open-type="switchTab" url="/pages/user/user">switchTab跳转到User页面</navigator>
    <button @click="show">显示</button>
    <button @click="hide">隐藏</button>
  </view>
</template>

<style lang="scss">

</style>