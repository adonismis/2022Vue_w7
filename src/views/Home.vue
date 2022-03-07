<template>
  <div class="home">
    Home
  </div>
</template>

<script>
export default {
  name: 'Home',
  mounted () {
    console.log(this.$http.get)
  }
}
</script>
