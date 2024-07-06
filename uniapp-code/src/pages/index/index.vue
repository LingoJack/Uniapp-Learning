<script setup>
import {onPullDownRefresh, onReachBottom, onReady} from "@dcloudio/uni-app";
import {computed} from "vue";

//存储接口返回数据的模型数组
const pets=ref([]);

//menu当前item的索引
const current=ref(0);

//menu分类数据源，这是根据接口加的，由于是接口固定功能，所以已经不需要ref了
const category=[
  {key:'all',value:'全部'},
  {key:'dog',value:'汪汪'},
  {key:'cat',value:'喵喵'}
]
//定义分类数据源的计算属性
const values=computed(()=>
  category.map((item)=>item.value)
)

//发送网络请求获取数据
function network(){
  uni.showNavigationBarLoading()
  uni.request({
    url:'https://tea.qingnian8.com/tools/petShow',
    data:{
      size:10,
      type:category[current.value].key
    },
    header:{

    }
  }).then(res=>{
    if (res.data.errCode===0){
      console.log(res.data)
      pets.value=[...pets.value,...res.data.data];
    }else {
      uni.showToast({
        title:res.data.errMsg,
        icon:"fail",
        duration:2000
      })
    }

  }).catch(err=>{
    uni.showToast({
      title:'请求有误，请重新刷新',
      icon:"none"
    })
  }).finally(()=>{
    console.log('调用结束')
    uni.hideNavigationBarLoading()
    //停止刷新
    uni.stopPullDownRefresh()
  })
}

onMounted(()=>{
  network();
})

/*这个函数会在下拉到最底下的时候触发*/
onReachBottom(()=>{
  let arr1=[1,2,3]
  let arr2=[4,5,6]
  console.log([arr1,arr2])// [1,2,3],[4,5,6]
  console.log([...arr1,...arr2]) //使用了解构符之后：[1,2,3,4,5,6]
  network();
})

//最上部下拉刷新
onPullDownRefresh(()=>{
  pets.value=[]
  current.value=0;
  network();
})

//点击预览
const preview=function (index){
  console.log(index)
  let urls=pets.value.map(e=>e.url)
  console.log(urls)
  //uni-api提供的图片预览接口
  uni.previewImage({
    current:index,
    urls:urls
  })
}

//刷新
const onRefresh=function (){
  console.log('刷新')
  uni.startPullDownRefresh()
}

//返回顶部
const onTop=function (){
  console.log('返回顶部')
  uni.pageScrollTo({
    scrollTop:0,
    duration:100
  })
}

//点击了menu的item触发的事件
function onClickItem(e){
  console.log(e)
  current.value=e.currentIndex;
  console.log("current index: "+current.value)

  //清空现有的pets数据
  pets.value=[];
  //重新发送请求
  network();
}

</script>

<template>
  <view class="container">

    <view class="menu">
      <uni-segmented-control
          :current="current"
          :values="values"
          @click-item="onClickItem"
          style-type="button"
          active-color="#2B9939"
      >

      </uni-segmented-control>
    </view>

    <view class="layout">
      <view class="box" v-for="(item,index) in pets" :key="item._id">
        <view class="pic">
          <!--     配置图片懒加载     -->
          <image :src="item.url" mode="widthFix" @click="preview(index)" lazy-load="true"/>
        </view>
        <view class="text">{{ item.content }}</view>
        <text class="author">by {{item.author}}</text>
      </view>

      <view class="float">
        <view class="item" @click="onRefresh">
          <!--     使用uni-ui扩展组件 uni-icons    -->
          <uni-icons type="refresh" size="26" color="#888"></uni-icons>
        </view>
        <view class="item" @click="onTop">
          <!--     使用uni-ui扩展组件 uni-icons    -->
          <uni-icons type="arrow-up" size="26" color="#888"></uni-icons>
        </view>
      </view>

      <!--   uni-ui扩展组件：下拉刷新   -->
      <view class="loadMore">
        <uni-load-more status="loading"></uni-load-more>
      </view>

    </view>
  </view>
</template>

<style lang="scss" scoped>
.container{
  .menu{
    padding: 25rpx 50rpx 0;
  }
  .layout{
    //设置左右间隔
    padding: 50rpx;
    .box{
      margin-bottom: 60rpx;
      box-shadow: 0 10rpx 30rpx rgba(0,0,0,0.08);
      border-radius: 12rpx;
      overflow: hidden;
      .pic{
        image{
          width: 100%;
        }
      }
      .text {
        padding: 30rpx;
        font-size: 36rpx;
      }
      .author{
        padding: 0 30rpx 30rpx;
        text-align: right;
        color:#888;
        font-size: 30rpx;
      }
    }

    .float{
      padding-bottom: env(safe-area-inset-bottom);
      position: fixed;
      right: 30rpx;
      bottom: 80rpx;
      .item{
        width: 90rpx;
        height: 90rpx;
        background-color: rgba(255,255,255,0.9);
        border-radius: 50%;
        margin-bottom: 20rpx;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px solid #eee;
      }
    }

    .loadMore{
      padding-bottom: calc(env(safe-area-inset-bottom) + 50rpx);
    }

  }
}
</style>