<script setup>
//同步方式设置APP缓存
uni.setStorageSync('myKey','myValue');

//同步获取APP缓存,如果不指定key则获取全部value
let myVal = uni.getStorageSync('myKey');
console.log(myVal)

setTimeout(()=>{
  //清除指定的缓存value
  uni.removeStorage({
    key:'myKey'
  })
},2000)

//清除全部的缓存，一般不使用
//uni.clearStorage();
</script>

<template>
  <!--
    uni.setStorage用于将数据存储在本地缓存中指定的key中，会覆盖掉原来该key对应的内容
    是一个异步接口
    比如：b站的搜索历史功能模块、浏览器搜索记录等

    具体的浏览器缓存可以在浏览器进入开发者页面，进入Application页面的Local storage查看

    一般都采用同步的形式来写
    异步的写法和同步的不同，主要在于success回调函数
    因为异步有一个必要要求：怎么让父线程知道自己（异步线程）已经完成了所需要的操作，这就是成功回调函数的职能
  -->



</template>

<style lang="scss">

</style>