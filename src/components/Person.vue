<template>
    <div class="person">
        <h2>name:{{ person.name }}</h2>
        <h2>age:{{ person.age }}</h2>

        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="showTel">显示电话</button>
    </div>
</template>

<script lang="ts" setup name="Person">

    import { ref,reactive,toRefs } from 'vue'

    let person =reactive({
        name:'zhang san',
        age:18,
    })

    let{name,age}=toRefs(person)

    function changeName(){
        name.value +='~',
        console.log(name.value,person.name)
    }

    function changeAge(){
        age.value++
    }

    // let name=ref("zhang san")
    // let age=ref(18)
    // let tel='13888888'

    // console.log(1,name)
    // console.log(2,age)

    // //方法
    // function changeName (){
    //     console.log(1)
    //     name.value ='li si'//页面无变化
    //     console.log(name)
    // }
    // function changeAge(){
    //     age.value += 1
    //     console.log(2)
    //     console.log(age)
    // }
    // function showTel(){
    //     alert(tel)
        
    // }
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