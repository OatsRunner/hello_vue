<template>
    <div class="person">
        familyName: <input type="text" v-model="familyName"><br>
        givenName: <input type="text" v-model="givenName"><br>
        Name:<span>{{ fullName }}</span><br>
        <button @click="changefullName">change Name</button>
    </div>
</template>

<script lang="ts" setup name="Person">
    import {ref,computed} from 'vue'
    
    let familyName=ref('zhang')
    let givenName=ref('san')

    // //如此定义的fullName只读，箭头函数有点跳出于知识框架了
    // let fullName=computed(()=>{
    //     return familyName.value.slice(0,1).toUpperCase()+familyName.value.slice(1)+
    //     ' '+givenName.value.slice(0,1).toUpperCase()+givenName.value.slice(1)
    // })

    //如此定义的fullName可读可写，箭头函数有点跳出于知识框架了
    let fullName=computed({
        get(){
            return familyName.value.slice(0,1).toUpperCase()+familyName.value.slice(1)+
            ' '+givenName.value.slice(0,1).toUpperCase()+givenName.value.slice(1)
        },
        set(val){
            console.log('set',val)
            const [str1,str2]=val.split(' ')
            familyName.value=str1
            givenName.value=str2
        }
    })

    function changefullName(){
        fullName.value='Li Si'
    }
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