<script setup>
/*
* showActionSheet是一个从底部向上弹出操作的api
* */
const arr=["研究生","本科","专科","高中","初中及以下"]
function select(){
  uni.showActionSheet({
    title:'请选择',
    // itemList:["研究生","本科","专科","高中","初中及以下"],
    itemList:arr,
    itemColor:'#000',
    //没有出现异常时候的回调函数，可以接收一个组件的返回时间作为参数
    success:res => {
      console.log(res)    //可以看到给出的是点击了数组索引
      //想要直接看到数组的项，可以这么写
      console.log('选择了：'+arr[res.tapIndex])
    }
  })
}


</script>

<template>
  <view>
    <button @click="select">选择受教育程度</button>
  </view>
</template>

<style lang="scss">

</style>