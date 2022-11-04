<template>
  <div 
  @dblclick="$emit('toggle-soldout', product.id)"
  :class="[product.soldout ? 'soldout' : '', 'product']">
      <h3>
          {{ product.title }} 
          <i @click="$emit('delete-product', product.id)" class="fas fa-times"></i>
      </h3>
      <p>{{ product.description }}</p>
      <p>{{ product.price }}</p>
  </div>
</template>

<script>
    export default{
        name: 'Product',
        props:{
          product: Object,
        },
    }
</script>

<style scope>
.fas {
  color: red;
}
.product {
  background: #292828;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.product.soldout {
  border-left: 5px solid green;
}
.product h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>