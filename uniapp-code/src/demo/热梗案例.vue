<!--  一个热梗小案例  -->
<script setup>
import {ref} from "vue";
const lists = ref([
  {id:111,title:"刚满18岁"},
  {id:222,title:"我不吃牛肉"},
  {id:333,title:"遥遥领先"},
  {id:444,title:"哪里贵了"}
])

function onClose(index){
  //数组元素的删除,index是要删除的下标，第二个参数是要删除的元素的个数
  lists.value.splice(index,1)
}

const inputVal=ref('');

function onSubmit(){
  if (inputVal.value.length<3){
    return;
  }
  lists.value.push({
    id: Date.now(),
    title: inputVal.value
  });
  inputVal.value='';

}


</script>

<template>
  <view class="title">
    近期热梗
  </view>

  <view class="out">
    <view class="list">
      <!--   将 item.id 设置为每个列表项的 key，以确保 Vue.js 能够正确地追踪和更新这些列表项，
             index是数组元素的索引，如果没有显式地设置key，会默认以index为key
      -->
      <view class="row" v-for="(item,index) in lists" :key="item.id">
        <view class="text">{{index+1}}. {{item.title}}</view>
        <view class="close">
          <icon type="clear" size="26" @click="onClose(index)"/>
        </view>
      </view>
    </view>
    <view class="count">
      共{{lists.length}}条梗
    </view>
    <view class="comment">
      <input type="text"
             placeholder="请输入热梗..."
             v-model="inputVal"
             @confirm="onSubmit"
      />
      <!--  :disable设置发布的要求是不少于三个字符    -->
      <button
          size="mini"
          type="primary"
          :disabled="inputVal.length<3"
          @click="onSubmit"
      >
        发布
      </button>
    </view>
  </view>
</template>


<style lang="scss" scoped>
.title{
  font-size: 26px;
  text-align: center;
  color:#3c3c3c;

  /*
  padding属性用于设置一个元素的内边距，即元素内容与其边框之间的空间
    1.padding-top: 5px;
    2.padding-right: 10px;
    3.padding-bottom: 15px;
    4.padding-left: 20px;
  如果都写在一起，那就是上、右、下、左的顺序
  */
  padding:30px 0 15px;
}
.out{
  width: 90vw;
  /*
  margin: 15px auto; 这个 CSS 规则应用于一个元素，它指定了上下外边距为 15px，
  而左右外边距则为自动，使得元素水平居中
  */
  margin:15px auto;
  box-shadow: 0 10px 20px rgba(0,0,0,0.1);
  border-radius: 5px;
  padding:15px;
  box-sizing: border-box;
  .list{
    .row{
      padding:10px 0;
      border-bottom:1px solid #e8e8e8;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 18px;
      color:#333;
      .text{
        padding-right: 5px;
        box-sizing: border-box;
      }
    }
  }
  .count{
    padding:10px 0;
    font-size: 15px;
    color:#888;
    text-align:center;
  }
  .comment{
    display: flex;
    margin-top:10px;
    input{
      flex:4;
      background: #f4f4f4;
      margin-right: 5px;
      height: 100%;
      height: 32px;
      border-radius: 4px;
      padding:0 10px;
      color:#333;
    }
    button{
      flex:1;
    }
  }
}

</style>
