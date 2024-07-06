<script setup>
import {ref} from "vue";

const count=ref(100)
function updateCount(){
  count.value++;
}


//之前讲的slot和emit都是单向数据源，还有其他办法可以直接向让父组件操作子组件的数据，即defineExpose
//defineExpose定义暴露的对象，父组件通过ref属性拿到子组件暴露出去的对象
defineExpose({
  //属性:值
  count:count,
  str:'LingoJack',
  //在defineExpose中可以暴露变量，也可以暴露函数
  updateCount:updateCount
})

</script>

<template>
  <view class="out">
    子组件count值：{{count}}
  </view>
</template>

<style scoped lang="scss">
.out{
  padding: 20px;
  background-color: #eeeeee;
}
</style>