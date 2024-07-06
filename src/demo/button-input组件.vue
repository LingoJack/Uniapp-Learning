<script setup>
import {ref} from "vue";
const count=ref(1)

setInterval(()=>{
  if (count.value<100){
    count.value++;
  }

  console.log(count)
},1000)

</script>

<template>
  <view>
    <!--  按钮的plain设置镂空，type改变按钮类型（颜色），size控制大小  -->
    <button size="mini" type="primary" plain="true">按钮</button>

    <!--  输入框标签只能自闭合  -->
    <input
        type="text"
        class="inputText"
        placeholder="输入框"
        placeholder-style="color:orange"
        maxlength="140"
    />

    <!--  ref定义响应式API，setInterval配置定时任务  -->
    <view>count: {{count}}</view>
  </view>
</template>

<style lang="scss">
.inputText{
  border: 1px solid grey;
}
</style>