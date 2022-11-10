<template>
  <div class="container">

    <Header 
    @toggle-add-product="toggleAddProduct"
    title = 'Product Tracker'
    :showAddProduct="showAddProduct" />

    <div v-show="showAddProduct">
      <AddProduct @add-product="addProduct" />
    </div>

    <Products
    @toggle-soldout="toggleSoldOut"
    @delete-product="deleteproduct"
    :products="products" />

  </div>
</template>

<script>
import Header from './components/Header.vue'
import Products from './components/Products.vue'
import AddProduct from './components/AddProduct.vue'

export default{
  name: 'App',
  components:{
    Header,
    Products,
    AddProduct
  },
  data(){
    return{
      products: [],
      showAddProduct: false
    }
  },
  methods:{
    toggleAddProduct(){
      this.showAddProduct = !this.showAddProduct
    },
    async addProduct(product){
      const res = await fetch('http://165.22.48.65:3000/products', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(product)
      })
      
      const data = await res.json()
      const validData = {
        id: data['newProduct']._id,
        title: data['newProduct'].title,
        description: data['newProduct'].description,
        price: data['newProduct'].price,
        soldout: data['newProduct'].soldout
      }
      this.products = [...this.products, validData]
    },
    async deleteproduct(id){
      if(confirm('Are you sure?')){
        const res = await fetch(`http://165.22.48.65:3000/products/${id}`, {
          method: 'DELETE'
        })
        
        res.status === 200
        ? (this.products = this.products.filter((product) => product.id !== id))
        : alert('Error deleting product')
      }
    },
    async toggleSoldOut(id){
      const soldOutProduct = await this.fetchProduct(id);
      const updProduct = {...soldOutProduct, soldout: !soldOutProduct.soldout}

      const res = await fetch(`http://165.22.48.65:3000/products/${id}`, {
        method: 'PATCH',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(updProduct)
      })

      const data = await res.json()
      this.products = this.products.map((product) => product.id === id ? 
      {...product, soldout : data.soldout} : product)
    },
    async fetchProducts(){
      const res = await fetch('http://165.22.48.65:3000/products')
      const data = await res.json()
      return data
    },
    async fetchProduct(id){
      const res = await fetch(`http://165.22.48.65:3000/products/${id}`)
      const data = await res.json()
      return data
    }
  },
  async created(){
    this.products = await this.fetchProducts()
  }
}
</script>

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
