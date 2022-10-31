<script setup>
    // 響應式狀態 用物件包起來的方式
    import { ref, reactive, watch} from 'vue';

    // *** ref 和 reactive 的差異 ***
    const num1 = ref({
    num: 0,
    }) 

    const num2 = reactive({
    num: 0,
    }) 
    const numRef = ref(0);
    
    const num3 = reactive({
        num: numRef,
    })

    console.log(num3.num); // result : 0 
    // 原因參考 https://cn.vuejs.org/api/reactivity-core.html
    // 響應式轉換是“深層”的：它會影響到所有嵌套的屬性。一個響應式對像也將深層地解包任何ref屬性，同時保持響應性。
    // 因此 在 reactive 中的 ref 不需要輸入 .value 因為已經解包了


    // 響應式狀態 用物件包起來的方式
    // reactive 只能包物件或陣列
    const person = reactive({
    name: 'Tom',
    age: 10,
    address: '台灣'
    }) 

    // 當 num1 被改變，執行後面的callback
    watch(num1, ()=>{
        console.log('num1 被改變了');
    });
    //  result : num1 不會被監聽 ！！！
    // 所以 ref 不能用物件包裝起來，會監聽不了
    // 除非要加上 {deep: true}
    // 或是直接改成 ref(0)

    // 當 num2 被改變，執行後面的callback
    watch(num2, ()=>{
        console.log('num2 被改變了');
    });


    setTimeout(()=>{
        num1.value.num = 100;
        num2.num = 100;
    },2000)

    setTimeout(()=>{
    person.name = 'Jerry',
    person.age = 20,
    person.address = '台北'
    },2000)


</script>

<template>
    <h1>ref 和 reactive</h1>
    <div>
        <p>{{person.name}}</p>  
        <p>{{person.age}}</p>  
        <p>{{person.address}}</p>  
    </div>
    <div>
        <h3>{{num1.num}}</h3>
        <h3>{{num2.num}}</h3>
    </div>
    <hr>
</template>