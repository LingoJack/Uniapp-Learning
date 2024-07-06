<script setup>
import {ref} from "vue";

const inputValue=ref('')
const isActive=ref(false)

function onFocus(event){
  isActive.value=!isActive.value;
  console.log(event)
}

function onBlur(event){
  isActive.value=!isActive.value;
  console.log(event)
}

function onInput(event){
  /*这个input事件其实就是v-model的实现原理，v-model是简化了这一过程*/
  console.log(event.detail.value);
  inputValue.value=event.detail.value;
}


</script>

<template>
  <!--表单的focus和blur以及input事件的用法演示-->
  <!--
  触发的函数可以接收一个返回值参数事件e，e的组成与更多细节详见浏览器控制台
    @focus:
      获取焦点时触发的事件
    @blur:
      失去焦点时触发的事件
    @input:
      在键入字符时触发的事件
    @confirm：
      在键入回车（确定）时触发的事件
   -->
  <view class="out">
    <!--  input组件必须自闭合  -->
    <input
        type="text"
        :value="inputValue"
        placeholder="请输入"
        @focus="onFocus"
        @blur="onBlur"
        @input="onInput"
        @confirm="console.log('onConfirm触发了')"
    />
    <image :class="isActive?'pic.active':'pic'" src="../../static/demo1/chicken.gif"></image>
  </view>

  <view class="preview">
    预览：{{inputValue}}
  </view>
</template>

<style lang="scss">
.out{
  /*padding第一个是间隔高距，第二个是间隔宽距*/
  padding:0 20px;
  margin-top: 40px;
  position: relative;
  input{
    border: 1px solid #f0ad4e;
    height: 40px;
    z-index: 2;
    position: relative;
    background-color: white;
    padding: 3px 10px;
  }
  .pic{
    width: 24px;
    height: 24px;
    z-index: 1;
    position: absolute;
    top: 0px;
    left: calc(50% - 12px);
    transition: top 0.3s;
  }
  .pic.active{
    top: -24px;
  }
}

.preview{
  padding: 20px 20px;
  border: 1px;
}


</style>