<script setup>
import { computed } from "@vue/reactivity";
import {reactive, ref, watch} from "vue";
const name = ref('mike');
// 直接呼叫 data 就會直接回傳內容


const index = ref(0);
const user = reactive({
    name: 'jerry',
    age: 28,
});

// computed 不能傳參數
const data = computed(()=>{
    return `my name is ${name.value}`;
})

const idxComputed = computed(()=>{
    return (index.value > 3) ? "這個大於三" : " 這個小於三 ";
})

const userComputed = computed(()=>{
    return `my name is ${user.name}, and my age is ${user.age}.`
})
setTimeout(()=>{
    name.value = 'Jerry';
    user.name = 'Henry';
    user.age = 18;
    index.value = 5;
},2000)

// get & set 

const count = ref(1);

const counter = computed({
    get:() => {
        return count.value;
    },
    set: (val) => {
        count.value = val;
    },
})

counter.value = 5;
console.log(counter.value);

</script>
<template>
    <div>
        <h3>{{data}}</h3>
        <h3>{{index}}</h3>
        <h3>{{idxComputed}}</h3>
        <h3>{{userComputed}}</h3>
    </div>
</template>