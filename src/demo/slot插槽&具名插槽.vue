<script setup>

import LingoLayout from "../../components/LingoLayout.vue";
</script>

<template>
  <!--  <lingo-layout>这是LingoJack的布局组件</lingo-layout>
        演示了具名插槽的使用方式，详见lingo-layout组件的注释：

        slot插槽：相当于占位符，未来可以通过父组件传递一段代码来替换占位符
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
            还需注意使用自定义组件需要导入
  -->
  <lingo-layout>
    <template v-slot:header>
      Header
    </template>
    <template #main>
      Main
    </template>
    <template #footer>
      Footer
    </template>
  </lingo-layout>
</template>

<style lang="scss" scoped>

</style>