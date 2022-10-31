<script setup>
import { ref, onMounted } from "vue";

// 響應式狀態
const count = ref(0);
const name = ref("Tom");

// 要取得 props
const props = defineProps({
  data: {
    type: Object,
    default: () => ({}),
  },
});
// 用来修改狀態、觸發更新的函數
function increment() {
  count.value++;
}

const changeName = () => {
  name.value === "Tom" ? (name.value = "Jerry") : (name.value = "Tom");
  console.log(name);
};

// 生命周期鉤子
onMounted(() => {
  console.log(`The initial count is ${count.value}.`);
});
</script>
<template>
    <h1 style="color: aliceblue">{{ count }}</h1>
    <br />
    <button @click="increment">Count is: {{ count }}</button>

    <h3>{{ name }}</h3>
    <button @click="changeName">changeName</button>
</template>