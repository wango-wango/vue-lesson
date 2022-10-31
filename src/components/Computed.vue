<script setup>
import { computed } from "@vue/reactivity";
import {reactive, ref, watch} from "vue";
const name = ref('mike');
const data = computed(()=>{
    return `my name is ${name}`;
})
</script>
<template>
    <div>
        <h3>{{data}}</h3>
    </div>
</template>