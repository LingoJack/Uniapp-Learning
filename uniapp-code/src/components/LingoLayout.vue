<script setup>

</script>

<template>
  <view class="layout">
    <view class="header">
      <slot name="header"></slot>
    </view>
    <view class="main">
      <!--  slot插槽：相当于占位符，未来可以通过父组件传递一段代码来替换占位符
            比如在index.vue页面中调用了LingoLayout组件，可以这么写来用代码替换slot插槽：
            <lingo-layout>这是LingoJack的布局组件</lingo-layout>
            lingo-layout标签中的内容将代替插槽的内容
            当然这是只有main区域有slot插槽的情况，如果footer或者header区域也需要高度定制化，
            即，也需要slot插槽
            那么为了知道那些代码是替换哪个区域的插槽，我们需要使用具名插槽
            即，<slot name="main"></slot>
            而其他页面要使用具名插槽指定插入组件的哪个区域
            可以这么写：
            <lingo-layout>
             <template v-slot:header></template>
             <template v-slot:main></template>
             <template v-slot:footer></template>
            </lingo-layout>
            或简写：
            <lingo-layout>
             <template #header></template>
             <template #main></template>
             <template #footer></template>
            </lingo-layout>
            如此

      -->
      <!--
        <slot></slot>
      -->
      <slot name="main"></slot>
    </view>
    <view class="footer">
      <slot name="footer"></slot>
    </view>
  </view>
</template>

<style scoped lang="scss">
.layout{
  .header{
    height: 100px;
    background-color: #cfcfcf;
  }
  .main{
    min-height: 200px;
    background-color: white;
  }
  .footer{
    height: 120px;
    background-color: orange;
  }
}
</style>