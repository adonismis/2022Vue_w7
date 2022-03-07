<template>
  <div class="row row-cols-1 row-cols-md-4 g-4">
    <div class="col" v-for="product in products" :key="product.id">
      <div class="card">
        <img :src="product.imageUrl" class="card-img-top" :alt="product.title">
        <div class="card-body">
          <h5 class="card-title">{{product.title}}</h5>
          <p class="card-text">{{product.content}}</p>
          <router-link class="btn btn-primary" :to="`/product/${product.id}`">詳細資料</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      products: []
    }
  },
  methods: {
    getProducts () {
      this.$http(`${process.env.VUE_APP_API}/api/${process.env.VUE_APP_PATH}/products/all`).then(
        (res) => {
          this.products = res.data.products
        }
      )
    }
  },
  mounted () {
    this.getProducts()
  }
}
</script>
