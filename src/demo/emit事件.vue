<script setup>
import EmitDemo from "../../components/EmitDemo.vue";
import {ref} from "vue";

const num=ref(0);
const color=ref('#fff')
function onAdd(event){
  console.log(event)
  num.value=event;
  color.value="#"+String(event).substring(3,6)
}

function onTest(event){
  console.log(event)
  num.value=event;
  color.value="#"+String(event).substring(3,6)
}




</script>

<template>
  <!--  emit的声明触发事件
    在slot插槽和prop中，是父组件向子组件传递信息（代码块或者属性值），这个信息是单向数据源
    而emit事件允许子组件向父组件传递信息

    子组件里是这么写的：
    <button @click="$emit('add',123)">按钮</button>

    所以在父组件中，用@add="onAdd"，这样onAdd可以接收到一个参数event
    这个event就是子组件通过$emit事件发送过来的数据，即123
    父组件中，
    function onAdd(event){
      console.log(event)    //控制台输出123
    }

    更多信息见EmitDemo组件
  -->
  <emit-demo @add="onAdd" @test="onTest"></emit-demo>
  <view class="box" :style="{background:color}">
    num:{{num}}
  </view>



</template>

<style lang="scss" scoped>
.box{
  padding: 20px;
  width: 100px;
  height: 100px;
}
</style>