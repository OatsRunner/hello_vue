<template>
    <div class="person">
        <h1>case1:监视ref定义的基本类型数据</h1>
        <h2>the sum is {{ sum }}</h2>
        <button @click="changesum">sum++</button>
        
        <h1>case2:监视ref定义的对象类型数据</h1>
        <h2>name:{{ person.name }}</h2>
        <h2>age:{{ person.age }}</h2>
        <button @click="changename">changename</button>
        <button @click="changeage">changeage</button>
        <button @click="changeperson">changeperson</button>

    </div>
</template>

<script lang="ts" setup name="Person">
    import {ref,watch} from 'vue'
    //data
    let sum=ref(0);

    let person=ref({
        name:'zhang san',
        age:18,
    })

    //function
    function changesum(){
        sum.value++
    }

    function changename(){
        person.value.name+='~'
    }

    function changeage(){
        person.value.age ++
    }

    function changeperson(){
        person.value={name:'li si',age:90}
    }

    //watch,case1
    const stopWatch = watch(sum,(newValue,oldValue)=>{
        console.log('sum changed',newValue,oldValue)
        if(newValue>=10){
            stopWatch()
        }
    })
    //case2，监视的是对象的地址值，若需要监视对象内部属性的变化，需手动开启深度监视
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