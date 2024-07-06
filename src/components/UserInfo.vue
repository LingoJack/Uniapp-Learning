<!--    这是一个组件，演示如何创建并使用组件
     1.prop父组件传值
     2.传值进来的prop是单向数据源，不可修改，但是可以通过计算属性达到修改输出的目的
     3.设置prop属性的默认值
     4.

  -->
<script setup>
//普通无默认值，无接收类型校验的写法
//const props = defineProps(['username','avatar']);

//如果要给prop属性设置接收的数据类型，可以这么写(即，给defineProps传递一个对象，可以带默认值)
const props=defineProps({
  username: {
    type:String,
    default:'匿名'
  },
  avatar:{
    type:String,
    default:'../static/demo1/pic4.jpg'
  }
})

// 还可以把username和avatar封装成一个对象：const props=defineProps(["obj"])
// 注意这里给defineProps传递的是数组，因为defineProps接收一个数组参数作为options选项，这是固定的写法
/*
* 如果设置props为一个对象，还要设置默认值可以这么写
defineProps({
  obj:{
    type:Object,
    default(){
      return {
        name:'匿名',
        avatar:'../static/demo1/pic4.jpg'
      }
    }
  }
})
* */






import {computed} from "vue";
const myname=computed(()=>{
  return props.username+'@'
})

console.log(myname.value)
</script>

<template>
  <view class="userInfo">
    <image class="avatar" :src="avatar"></image>
    <view class="username">{{ username }}</view>
  </view>
</template>

<style scoped lang="scss">
.userInfo{
  width: 100%;
  height: 175px;
  background-color: #ccc;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  image{
    width: 100px;
    height: 100px;
    border-radius: 50%;
  }
  .username{
    padding: 10px 0;
    font-size: 20px;
  }

}


</style>