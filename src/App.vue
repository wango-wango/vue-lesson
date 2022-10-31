<!-- <script>
// --- Options API 的寫法 比較接近 vue2 ---\\

export default {
  components: {
    HelloWorldVue,
  },
  props:{
    data: {
      type : Object,
      default : () => ({})
    }
  },
  data() {
    return {
      count: 0,
    };
  },

  methods: {
    increment() {
      this.count++;
    },
  },

  mounted() {
    console.log(`The initial count is ${this.count}.`);
  },
};
</script>  -->
<script setup>
// -- composition API -- \\

// 呼叫外部component
import HelloWorldVue from "./components/HelloWorld.vue";
import RefReactive from "./components/RefReactive.vue";
import RefFunctionOnMountedVue from "./components/RefFunctionOnMounted.vue";
import ComputedVue from "./components/Computed.vue";
</script>

<template>
  <div>
    <HelloWorldVue />
    <hr>
    <RefFunctionOnMountedVue />
    <hr>
    <RefReactive />
    <hr>
    <ComputedVue />
  </div>
</template>

<style>

</style>
