<script>
    export default{
        name: 'Product',
        props:{
            item: Object,
        },
    }
</script>

<template>
    <div class="product">
        <h3>
            {{ item.title }} 
            <i class="fas fa-times"></i>
        </h3>
        <p>{{ item.description }}</p>
        <p>{{ item.price }}</p>
    </div>
</template>

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
.product.reminder {
  border-left: 5px solid green;
}
.product h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>