<template>
  <div class="row">
    <div class="col-sm-4">
      <div><router-link class="btn btn-primary" to="/products">回上頁</router-link></div>
      評價星級：{{product.star}}
      <hr />
      主圖：
      <div class="mb-2">
        <img
          class="img-fluid"
          :src="product.imageUrl"
          alt=""
          v-if="product.imageUrl != ''"
          onerror="this.src='https://media.istockphoto.com/photos/frolic-smiling-pug-puppy-dog-with-yellow-constructor-helmet-holding-picture-id1127384534?s=612x612'"
        />
      </div>
      <hr />
      次圖圖片：
      <div class="mb-3" v-for="(image, index) in product.imagesUrl" :key="index">
        <img
          :src="product.imagesUrl[index]"
          :alt="product.title + '_img' + index"
          class="img-fluid"
        />
      </div>
    </div>
    <div class="col-sm-8">
      <div class="mb-3">
        <h1>{{product.title}}</h1>
        <button type="button" class="btn btn-outline-success">{{product.category}}</button>
      </div>
      <div class="row">
        <div class="mb-3 col-md-6">
          <label for="origin_price" class="form-label">原價</label>
          {{product.origin_price}} 元
        </div>
        <div class="mb-3 col-md-6">
          <label for="price" class="form-label">售價</label>
          {{product.price}} 元
        </div>
      </div>
      <hr />
      <div class="mb-3">
        <label for="description" class="form-label">產品描述</label>
        {{product.description}}
      </div>
      <div class="mb-3">
        <label for="content" class="form-label">說明內容</label>
        {{product.content}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      product: ''
    }
  },
  methods: {
    getProducts () {
      this.$http(
        `${process.env.VUE_APP_API}/api/${process.env.VUE_APP_PATH}/product/${this.$route.params.id}`
      ).then((res) => {
        console.log(res)
        this.product = res.data.product
      })
    }
  },
  mounted () {
    console.log(this.$route)
    this.getProducts()
  }
}
</script>
