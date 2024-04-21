<template>
    <div class="car">
        <h2>a {{ car.brand }} car,price {{ car.price }}</h2>
        <button @click="changePrice">change price</button>

        <hr>
        <h2>game list:</h2>
        <ul>
            <li v-for="g in games" :key="g.id">{{g.name }}</li>
        </ul>
        <button @click="changefirst">changefirst</button>
        
        <h2>sum is{{ sum }}</h2>
        <button @click="sumplus">sum++</button>
    </div>
</template>

<script lang="ts" setup name="Car">
    import { reactive,ref } from 'vue'

    let car =ref({brand:'Benz',price:100})
    let games=ref([
        {id:'001',name:'genshin'},
        {id:'002',name:'mihoyo'},
        {id:'003',name:'hokai'}
    ])

    let sum=ref(0)

    function changePrice(){
        car.value={brand:'BMW',price:1};
    }//ref修改对象
    // function changePrice(){
    //     Object.assign(car,{brand:'BMW',price:1});
    // }reactvie修改对象

    function changefirst(){
        games.value[0].name='starrail'
    }

    function sumplus(){
        sum.value++;
    }

</script>

<style scoped>

    .car{
        background-color: skyblue;
        box-shadow: 0 0 10px;
        border-radius: 10px;
        padding: 20px;
    }
    button{
        margin:0 5px
    }
</style>