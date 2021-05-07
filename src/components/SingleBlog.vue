<template>
  <div id="single-blog">
    <h1>{{blog.title}}</h1>
    <article>{{blog.content}}</article>
    <p>作者：{{blog.author}}</p>
    <ul>
      <li v-for="category in blog.categories" :key="category">{{category}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'single-blog',
  data () {
    return {
      id: this.$route.params.id,
      blog: {}
    }
  },
  created () {
    this.$http.get('https://myblog-2021-3bfc5-default-rtdb.firebaseio.com/posts/' + this.id + '.json/')
      .then(function (data) {
        console.log(data)
        return data.json()
        // this.blog = data.body
      })
      .then(function (data) {
        this.blog = data
      })
  }
}
</script>

<style>
#single-blog{
  max-width: 960px;
  margin: 0 auto;
  padding: 20px;
  background: lightgray;
  border: 1px dotted #aaa;
}
</style>
