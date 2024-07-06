<script setup>
import {ref,watch,watchEffect} from "vue";
const person=ref(1);

/*watch监听事件，第一个参数是要监听的交互式变量(字符串或者数字)，
* 第二个参数是函数
* 函数的参数第一个是交互式变量的旧值，第二个是交互式变量的新值
*
* 如果watch第一个参数不是交互式的字符串或数字，而是交互式的对象，
* 那么必须用.value属性
*
* 当要监听的是一个交互式对象，可以用一个箭头函数去指定具体监听这个对象的什么字段
* watch(()=>{persion.value.name},(oldValue,newValue)=>{...})
*
* 如果不清楚到底什么发生了改变，那么可以用深度监听
* watch(persion,(oldValue,newValue)=>{...},{deep:true,immediate:true}
* */
watch(person,(value, oldValue,newValue)=>{
  console.log(oldValue);
  console.log(newValue)
})

watchEffect(()=>{
  /*watchEffect不需要指定监听的对象，任何数据源发生改变，watchEffect就会触发*/
  console.log('something changed')
})


</script>

<template>
  <view class="out">
    <input type="text" v-model="person"/>
  </view>
</template>

<style lang="scss" scoped>

</style>