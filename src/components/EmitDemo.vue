<script setup>
import {ref} from "vue";

const emit=defineEmits(["test"])

function onClick(){
  emit('test',Math.random())
}


</script>

<template>
  <view>
    子组件向父组件发送信息——Emit演示
    <button @click="$emit('add',Math.random())">向父组件发送随机数</button>

    <!--    -->
    <button @click="onClick">按钮</button>
  </view>
</template>

<style scoped lang="scss">

</style>