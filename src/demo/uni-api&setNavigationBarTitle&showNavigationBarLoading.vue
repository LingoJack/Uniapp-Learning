<script setup>
/*
* uni-api提供了setNavigationBarTitle来动态设置页面的导航标题，而不仅仅在pages.json里面写死
* 类似的还有uni.setNavigationBarColor()
* */
uni.setNavigationBarTitle({
  title:'动态标题'
})

//设置导航栏读取进度条样式
uni.showNavigationBarLoading();

//两秒之后改变标题和导航栏的加载状态样式
setTimeout(()=>{
  uni.setNavigationBarTitle({
    title:'标题变化了'
  })
  uni.hideNavigationBarLoading();
},2000)

</script>

<template>

</template>

<style lang="scss">

</style>