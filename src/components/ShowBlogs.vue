<template>
  <div id="show-blogs">
    <h1>博客总览</h1>
    <div class="single-blog"></div>
  </div>
</template>

<script>
export default {
  name: 'show-blogs',
  data: function () {
    return {

    }
  },
  created () {
    this.$http.get('https://jsonplaceholder.typicode.com/posts')
      .then(function (data) {
        // console.log(data)
        this.blogs = data.body.slice(0, 10)
        console.log(this.blogs)
      })
  }
}
</script>

<style>

</style>
