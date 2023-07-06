<!-- 請建立 MyBadge.vue 元件，並支援下列功能
color 能夠設定背景顏色
text-color 能夠設定文字顏色
label 能夠設定文字內容
rounded 樣式
參考:https://quasar.dev/vue-components/badge/ -->

<script>
export default {
  props: {
    color: String,
    textColor: String,
    label: String,
    rounded: Boolean,
  },
};
</script>

<template>
  <div
    class="badgeExample"
    :style="{
      background: color,
      color: textColor,
      borderRadius: rounded ? '50px' : '0',
    }"
  >
    {{ label }}
  </div>
</template>

<style>
.badgeExample {
  line-height: 0.1rem;
  font-size: 0.8rem;
  display: inline-block;
  border: 1px solid black;
  font-weight: 700;
  padding: 0.4rem;
  /* vertical-align: top; */
}
</style>
