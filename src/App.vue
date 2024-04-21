<template>
    <!--html-->
    <div class="app">
        <h1>hello!</h1>
        <person/>
        <car/>
    </div>
</template>

<script>
    // js/ts
    import Person from './components/Person.vue';
    import Car from './components/Car.vue';

    export default{
        name:'App',//组件名c
        components:{Person,Car}//注册组件
    }
</script>

