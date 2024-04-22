<template>
    <div class="person">
        
        <h1>case3:监视reactie定义的对象类型数据</h1>
        <h2>name:{{ person.name }}</h2>
        <h2>age:{{ person.age }}</h2>
        <button @click="changename">changename</button>
        <button @click="changeage">changeage</button>
        <button @click="changeperson">changeperson</button>
        <
    </div>
</template>

<script lang="ts" setup name="Person">
    import {reactive,watch,computed} from 'vue'
    //data

    let person=reactive({
        name:'zhang san',
        age:18,
    })

    //function


    function changename(){
        person.name+='~'
    }

    function changeage(){
        person.age ++
    }

    function changeperson(){
        Object.assign(person,{name:'li si',age:90})
        //利用Object.assign类似于强行批量替换对象内的元素，但是ref可以直接替换person对象
    }

    //case3，监视的是reactive对象的地址值，若需要监视对象内部属性的变化，默认开启深度监视
    //watch第一个参数是被监视的数据
    //watch第二个参数是监视回调
    //watch第三个参数是配置
    watch(person,(newValue,oldValue)=>{
        console.log('personchanged',newValue,oldValue)
    },{deep:true,immediate:true}/*watch的属性 */)

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