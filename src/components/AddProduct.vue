<template>
    <form @submit="onSubmit" class="add-form">

    <div class="form-control">
      <label>Title</label>
      <input type="text" v-model="title" name="title" placeholder="Add Title" />
    </div>

    <div class="form-control">
      <label>Description</label>
      <input type="text" v-model="desc" name="desc" placeholder="Add Description" />
    </div>

    <div class="form-control">
      <label>Price</label>
      <input type="number" v-model="price" name="price" placeholder="Add Price" />
    </div>

    <div class="form-control form-control-check">
      <label>Sold Out</label>
      <input type="checkbox" v-model="soldout" name="soldout" />
    </div>

    <input type="submit" value="Save Product" class="btn btn-block" />
  </form>
</template>

<script>
    export default{
        name:'AddProduct',
        data(){
            return {
                title: '',
                desc: '',
                price: '',
                soldout: false
            }
        },
        methods:{
            onSubmit(e){
                e.preventDefault()
                
                if(!this.title){
                    alert('Please add a title')
                }
                if(!this.desc){
                    alert('Please add a description')
                }
                if(!this.price){
                    alert('Please add a price')
                }

                const newProduct ={
                    id: Math.floor(Math.random() * 100000),
                    title: this.title,
                    desc: this.desc,
                    price: this.price,
                    soldout: this.soldout
                }
                
                this.title = '';
                this.desc = '';
                this.price = '';
                this.soldout = '';

                this.$emit('add-product', newProduct);
            }
        }
    }
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>