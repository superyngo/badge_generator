<!-- 請建立 MyBadge.vue 元件，並支援下列功能
color 能夠設定背景顏色
text-color 能夠設定文字顏色
label 能夠設定文字內容
rounded 樣式
參考:https://quasar.dev/vue-components/badge/ -->

<script>
export default {
  props: { MyBadgeProps: {} },
};
</script>

<template>
  <div
    class="badgePreview"
    :style="{
      background: MyBadgeProps.color,
      color: MyBadgeProps.textColor,
      borderRadius: MyBadgeProps.rounded ? '50px' : '0px',
    }"
  >
    {{ MyBadgeProps.label }}
  </div>
</template>

<style>
.badgePreview {
  line-height: 1rem;
  font-size: 2rem;
  display: inline-block;
  border: 1px solid black;
  font-weight: 700;
  padding: 0.5rem;
  /* vertical-align: top; */
}
</style>
