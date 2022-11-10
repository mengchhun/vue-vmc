<template>
    <header>
        <h1> {{title}} </h1>
        <Button
        @btn-click="$emit('toggle-add-product')"
        :text="showAddProduct ? 'Close': 'Add'" 
        :color="showAddProduct? 'red': 'green'"
        />
    </header>
</template>

<script>
import Button from './Button.vue'

export default{
    name: 'Header',
    props: {
        title: String,
        showAddProduct: Boolean
    },
    components: {
        Button,
    },
    emits: ['toggle-add-product']
}
</script>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>