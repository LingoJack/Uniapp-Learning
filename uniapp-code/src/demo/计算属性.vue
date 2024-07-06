<script setup>
import {ref} from "vue";

const firstName=ref('')
const lastName=ref('')

/*
computed属性，即计算属性.computed属性是为了减少template中响应式变量的计算的臃肿性而存在的
不用computed：全名：{{firstName+'-'+lastName}}
用computed：全面：fullName

其实使用函数也能达到一样的效果，只是计算属性具有缓存性，而函数没有，每次都需要重新运算，
所以使用计算属性可以在一定程度上提高性能
*/
import {computed} from "vue";
const fullName=computed(()=>{
  return firstName.value+'-'+lastName.value;
})



</script>

<template>
  <view class="out">
    <input type="text" v-model="firstName" placeholder="请输入名"/>
    <input type="text" v-model="lastName" placeholder="请输入姓"/>
    <view>全名：{{fullName}}</view>
  </view>
</template>

<style lang="scss" scoped>
.out{
  padding: 20px;
  input{
    border: 1px solid #888888;
    height: 40px;
    /*margin: 15px auto; 这个 CSS 规则应用于一个元素，第一个参数是上下边距，第二个是左右边距*/
    margin: 10px 0;
    padding: 0 10px;
  }
}

</style>
