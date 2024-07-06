<script setup>

</script>

<template>
  <!--
      可以在src下创建一个common目录，新建css目录添加css文件
      在需要使用该样式的页面的style区域@import引入即可使用

      这里不放在static目录中是因为有一些样式我们不一定会用到，但是static目录下的所有文件都会被打包
      所以建议是新建common目录放置

      也可以在src/common下创建scss目录，里面可以创建scss样式文件
      使用方法同css的@import。

      在scss中，要定义变量：
      $uni-color-primary: #007aff;
      自己的scss文件要编译进项目，需要把自己的scss文件在uni-scss文件中@import
      要在自己的scss文件使用，color:$uni-color-primary即可
   -->
  <view>
    @import导入css样式以及scss变量用法与static目录演示
    <br/>
    <text>scss变量使用的演示</text>
  </view>
</template>

<style lang="scss" scoped>
@import "../../common/css/style.css";
text{
  color: $custom-color-1;
}
</style>