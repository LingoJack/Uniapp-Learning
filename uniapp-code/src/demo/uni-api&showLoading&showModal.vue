<script setup>

/*
showLoading是另一个uni-api，显示加载弹窗，默认不会主动消失，要自己设置定时器*
通常这个时间会用来从后端获取数据
/
 */
uni.showLoading({
  title:'Loading',
  mask:true,
})

//设置定时器，执行一次就是setTimeout，多次就是setInterval
setTimeout(()=>{
  uni.hideLoading();
},500)

function remove(){
  /*showModel是出一个默认弹窗，有确定和取消两个按钮*/
  uni.showModal({
    //弹窗标题
    title:'确定要删除吗？',
    //弹窗内容
    content:'删除后数据将无法恢复',
    //取消键的文本样式
    cancelText:'No',
    cancelColor:'#999999',
    //确认键的文本样式
    confirmText:'Yes',
    confirmColor:'#f00',
    //控制是否显示输入框，里面是content的内容
    editable:true,
    //未出现异常时候的回调函数，可以接收一个组件的返回时间作为参数
    success:res=>{
      console.log(res)
      //根据res的内容可以判断用户点击了确定还是取消，处理响应的逻辑
      if (res.confirm){
        console.log('删除成功')
        uni.showToast({title:'删除成功'})
      }
      else if (res.cancel) {
        console.log('取消删除')
        uni.showToast({title:'取消删除'})
      }
    },
    //出现异常时候的回调函数,可以接收一个组件的返回事件作为参数
    fail:err=>{
      console.log(err)
      console.log('发生了异常')
    }



  })
}

</script>

<template>
  <view>
    <button @click="remove">删除</button>
  </view>
</template>

<style lang="scss">

</style>