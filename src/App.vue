<script>
import MyBadgePreview from "./MyBadgePreview.vue";
import MyBadge from "./MyBadge.vue";

export default {
  components: { MyBadgePreview, MyBadge },
  data() {
    return {
      post: {
        color: "white",
        textColor: "black",
        label: "",
        rounded: "",
      },
      badgeExamples: [],
    };
  },
  methods: {
    putExample() {
      this.badgeExamples.push({ ...this.post });
      console.log(this.badgeExamples);
    },
  },
  watch: {
    post: {
      deep: true,
      handler() {
        localStorage.setItem("myBadgerPost", JSON.stringify(this.post));
      },
    },
    badgeExamples: {
      deep: true,
      handler() {
        localStorage.setItem(
          "badgeExamples",
          JSON.stringify(this.badgeExamples)
        );
      },
    },
  },
  mounted() {
    this.post = JSON.parse(localStorage.getItem("myBadgerPost")) ?? this.post;
    this.badgeExamples =
      JSON.parse(localStorage.getItem("badgeExamples")) ?? this.badgeExamples;
  },
};
</script>

<template>
  <div class="body">
    <div class="inputContainer">
      <label>
        請選擇背景顏色
        <input type="color" class="colorInput" v-model="post.color" />
      </label>
      <label>
        請選擇文字顏色
        <input type="color" class="colorInput" v-model="post.textColor" />
      </label>
      <input
        class="labelInput"
        type="text"
        v-model="post.label"
        placeholder="請輸入badge內文"
      />
      <label>
        是否有圓角
        <input class="roundedInput" type="checkbox" v-model="post.rounded"
      /></label>
      <button @click="putExample">存成範例</button>
    </div>
    <div class="previewContainer">
      <h1>Preview</h1>
      <MyBadgePreview :MyBadgeProps="post" />
      <h1>Examples</h1>
      <div class="MyBadgeExamples">
        <MyBadge label="NewLabel" color="red" rounded />
        <MyBadge label="NewLabel" textColor="red" rounded />
        <MyBadge label="" color="green" rounded />
        <MyBadge
          v-for="badgeExample of badgeExamples"
          :label="badgeExample.label"
          :textColor="badgeExample.textColor"
          :color="badgeExample.color"
          :rounded="badgeExample.rounded"
        />
      </div>
    </div>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
}
.body {
  max-width: 80%;
  min-height: 80svh;
  display: flex;
}
.body > * {
  flex-basis: 100%;
}
.inputContainer {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}
.previewContainer {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}
.MyBadgeExamples {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>
