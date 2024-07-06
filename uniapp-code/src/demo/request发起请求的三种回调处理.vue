<script setup>
const arr=ref([

])

/*
* uni.request是用来发起网络请求的api
* url 请求地址
* data 请求参数
* header 请求头
* method 请求方法
* timeout 设置超时时间
* */
function request(){
  uni.request({
    url:'https://jsonplaceholder.typicode.com/posts',
    //成功的回调函数，但实际开发中用得不多，而是另一种then的写法
    // success:res=>{
    //   console.log(res)
    //   arr.value=res.data;
    // }
  }).then(res=>{
    console.log(res)
    arr.value=res.data;
  })
}

/*其实除了success回调函数和then函数，还有另一种写法：异步同步化*/
async function anotherRequest(){

  let res=await uni.request({
    url:'https://jsonplaceholder.typicode.com/posts'
  })
  console.log(res)
  arr.value=res.data;
  return res;
}

</script>

<template>
  <view class="layout">
    <button @click="request">测试uni.request</button>
    <button @click="anotherRequest">测试异步函数同步等待方式请求</button>
    <view class="main">
      返回得到的数据回显：
      <br/>
      <view class="row" v-for="item in arr">
        <view class="title">{{item.title}}</view>
        <view class="content">{{item.body}}</view>
      </view>
    </view>
  </view>
</template>

<style lang="scss">
.layout{
  padding: 30rpx;
  .row{
    border-bottom: 1px solid #cfcfcf;
    padding: 20rpx 0;
    .title{
      font-size: 36rpx;
    }
    .content{
      font-size: 28rpx;
      color: #666;
    }

  }
}
</style>