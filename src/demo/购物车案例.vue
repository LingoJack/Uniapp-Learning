<script setup>
import {computed, ref} from "vue";

const goods=ref([
  {id:"1",name:'小米',price:4999},
  {id:"2",name:'华为',price:6899},
  {id:"3",name:'OPPO',price:4999},
  {id:"3",name:'Apple',price:9888}
])

const remove=(index)=>{
  goods.value.splice(index,1)
}

const selectedGroup=ref([])
const totalNum=computed(()=>selectedGroup.value.length)
const totalPrice=computed(()=>{
  let total=0
  goods.value.forEach((item)=>{
    if (selectedGroup.value.includes(item.id)){
      total+=item.price;
    }
  })
  return total;
})

function itemChange(event){
  console.log(event);
  selectedGroup.value=event.detail.value;
}








</script>

<template>
  <!-- checkbox-group的@change在复选框组的任何一个复选框的选中状态改变时触发，可以接收一个事件e参数，具体参见控制台 -->
  <checkbox-group @change="itemChange">
    <view class="out" v-for="(item,index) in goods" :key="item.id">
      <checkbox :value="item.id"></checkbox>
      <text class="title">{{item.name}}</text>
      <text class="price">￥{{item.price}}</text>
      <!--  index应该理解为数组下标，删除了数组的话下标也会改变  -->
      <text class="del" @click="remove(index)">删除</text>
    </view>
  </checkbox-group>
  <view class="card">
    <view class="text">选中了{{totalNum}}个商品，总计{{totalPrice}}元</view>
  </view>
</template>

<style lang="scss" scoped>
/*scoped的意思是：这里的scss文件仅用于当前vue组件，防止造成样式污染*/
.out{
  /*控制项与项之间的间距*/
  padding: 3px;
  .price{
    margin-left: 30px;
  }
  .del{
    color: #dd524d;
    margin-left: 30px;
  }
}
.card{
  margin-top: 30px;
  border-top:1px solid #eee;
  padding: 10px 0;
}
</style>