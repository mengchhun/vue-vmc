<script>
import Product from './Product.vue'
    export default{
        name: 'Products',
        props:{
            items: Array,
        },
        components:{
            Product,
        },
    }
</script>

<template>
    <div :key="item.id" v-for="item in items">
        <Product :item="item"/>
    </div>
</template>