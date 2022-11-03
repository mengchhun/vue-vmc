<script>
import Buttom from './Button.vue'

export default{
    name: 'Header',
    props: {
        title: String,
    },
    components: {
        Buttom,
    }
}
</script>

<template>
    <header>
        <h1> {{title}} </h1>
        <Buttom text="Add Product" color="green"/>
    </header>
</template>


<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>