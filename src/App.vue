<script>
import Header from './components/Header.vue'
import Products from './components/Products.vue'

export default{
  name: 'App',
  components:{
    Header,
    Products,
  },
  data(){
    return{
      tasks: []
    }
  },
  created(){
    this.items = [
    {
      title: 'test title 1',
      description: 'test desc 1',
      price: 12.34
    },
    {
      title: 'test title 2',
      description: 'test desc 2',
      price: 45.67
    },
    {
      title: 'test title 3',
      description: 'test desc 3',
      price: 78.90
    }
  ]}
}
</script>

<template>
  <div class="container">
    <Header title = 'Product Generator'/>
    <Products :items="items" />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
