<template>
    <div class="person">
        <h2>name:{{ person.name }}</h2>
        <h2>age:{{ person.age }}</h2>
        <h2>car:{{ person.car.c1 }} {{ person.car.c2 }}</h2>
        <button @click="changeName">changeName</button>
        <button @click="changeAge">changeAge</button>
        <button @click="changeC1">changeC1</button>
        <button @click="changeC2">changeC2</button>
        <button @click="changeCar">changeCar</button>
    </div>
</template>

<script lang="ts" setup name="Person">
    import {reactive,watch} from 'vue'
    //data
    let person =reactive({
        name:"zhang san",
        age:18,
        car:{
            c1:"benz",
            c2:"BMW"
        }
    })
   
    //function
    function changeName(){
        person.name+='~'
    }
    function changeAge(){
        person.age+=1
    }
    function changeC1(){
        person.car.c1='audi'
    }
    function changeC2(){
        person.car.c2='volks'
    }
    function changeCar(){
        person.car={c1:'yadi',c2:'aima'}
    }
    //case4，监视reactive对象内某个属性
    //getter能返回一个值的函数
    watch(()=>{return person.name},(newValue,oldValue)=>{
        console.log('changed',newValue,oldValue)
    })
    //case4，监视reactive对象内某个属性,且该对象为对象类型可以直接写也可以写函数，推荐写函数
    watch(()=>{return person.car},(newValue,oldValue)=>{
        console.log('carchanged',newValue,oldValue)
    },{deep:true})

</script>

<style scoped>

    .person{
        background-color: skyblue;
        box-shadow: 0 0 10px;
        border-radius: 10px;
        padding: 20px;
    }
    button{
        margin:0 5px
    }
</style>