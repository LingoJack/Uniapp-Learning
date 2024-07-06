<script setup>
/*动态修改TarBar的某一项的api：uni.setTabBarItem
* 这个一般放在App.vue的onLaunch那里
* */
uni.setTabBarItem({

})

//隐藏TabBar
uni.hideTabBar()
//两秒钟后显示TabBar
setTimeout(()=>{
  uni.showTabBar()

  /*
    为TabBar某一项的右上角添加文本，这个也一般放在App.vue的onLaunch那里
    可以在项对应的页面的onShow把text删除来实现已读取消
  */
  uni.setTabBarBadge({
    //说明为哪一项添加，最左边为第一项，索引0
    index:1,
    //指定添加的文本
    text:"3",
  })
  //显示TabBar某一项右上角小红点，可以在项对应的页面的onShow调用uni.hideTabBarRedDot来实现已读取消
  uni.showTabBarRedDot({
    //说明为哪一项添加，最左边为第一项，索引0
    index:0
  })
},800)



</script>

<template>

</template>

<style lang="scss">

</style>