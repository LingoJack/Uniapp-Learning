<script setup>
import DefineExposeComponent from "../../components/defineExposeComponent.vue";
import {ref,onMounted} from "vue";

const child=ref(null)
console.log(child.value)    //由于还没有渲染DOM体，所以现在还是拿不到子组件的ref暴露对象的
onMounted(()=>{
  console.log(child.value)    //onMounted钩子函数将在组件挂载完毕渲染DOM后使用，这里可以拿到子组件暴露的ref
})

//当按钮的点击事件触发的时候，DOM一定已经渲染完毕了
function update(){
  child.value.updateCount()
}

</script>

<template>
  <!--
    之前讲的slot和emit都是单向数据源，还有其他办法可以直接向让父组件操作子组件的数据，即defineExpose
    defineExpose定义暴露的对象，父组件通过ref属性拿到子组件暴露出去的对象。
    子组件可以通过在defineExpose暴露的对象中写上变量和函数的属性:值，父组件可以这么调用从子组件中ref得到的函数：
    child.value.updateCount()
  -->
  <view class="layout">
    <define-expose-component ref="child"></define-expose-component>
    <text>-----------以下是父组件内容-----------</text>
    <button @click="update">修改Count的值</button>
  </view>
</template>

<style lang="scss" scoped>

</style>