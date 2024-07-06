<script setup>
/*导入下拉触底刷新*/
import {onReachBottom} from "@dcloudio/uni-app";

/*这个函数会在下拉到最底下的时候触发*/
onReachBottom(()=>{
  console.log('到底了')
})


</script>

<template>
  <view v-for="item in 100">
    {{item}}
  </view>
</template>

<style lang="scss">

</style>