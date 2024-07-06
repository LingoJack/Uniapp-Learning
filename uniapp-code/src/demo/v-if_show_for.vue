<script setup>
import {ref} from "vue";
const isActive=ref(false)

const changeShop=()=>{
  isActive.value=!isActive.value;
}

const list=([
  {id:1,name:"John",num:23},
  {id:2,name:"Jans",num:6},
  {id:3,name:"Lingo",num:15}
])

</script>

<template>
  <!-- 演示条件渲染v-if -->
  <view class="shop">
    <view v-if="isActive">京东</view>
    <view v-else>淘宝</view>
    <button @click="changeShop">改变商店</button>

    <!-- v-show则是通过style的display的属性进行隐藏的 -->
    <view v-show="isActive">
      <text>display:none</text>
    </view>

    <!--  演示v-for，一般不建议用index作为唯一的标识(因为删除可能会出现index重复)，而是在list的元素里增加一个唯一的id属性标识  -->
    <view v-for="(item,index) in 10">
      Hello World-{{index}}
    </view>
    <view v-for="(item,index) in list">
      info({{index}}):My name is {{item.name}},player-{{item.num}}
    </view>

  </view>
</template>

<style lang="scss" scoped>
/*scoped的意思是：这里的scss文件仅用于当前vue组件，防止造成样式污染*/

</style>