<script setup>
import {ref,onMounted,onUnmounted} from "vue";

//这时候还拿不到scroll-view的属性，因为组件还没有挂载完毕
const scroll=ref(null);
console.log(scroll.value)   //输出null，因为没拿到

onMounted(()=>{
  console.log('mounted钩子函数调用了')
  console.log(scroll.value)   //输出具体的scroll-view组件的返回值
})

onUnmounted(()=>{
  console.log('unmounted钩子函数调用了')
})



</script>

<template>
  <view class="layout">
    <sroller-view scroll-y="true" class="scroll" ref="scroll">
      <view>
        前端钩子函数演示
      </view>
    </sroller-view>
  </view>
</template>

<style lang="scss" scoped>

</style>