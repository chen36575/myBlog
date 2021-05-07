<template>
  <div  v-theme:column="'narrow'" id="show-blogs">
    <h1>博客总览</h1>
    <input type="text" v-model="search" placeholder="搜索">
    <div v-for="blog in filteredBlogs" :key="blog" class="single-blog">
      <router-link :to="'/blog/' + blog.id">
        <h2>{{blog.title | to-upperCase}}</h2>
      </router-link>
      <article>
        {{blog.content | snippet}}
      </article>
    </div>
  </div>
</template>

<script>
export default {
  name: 'show-blogs',
  data: function () {
    return {
      blogs: [],
      search: ''
    }
  },
  created () {
    this.$http.get('https://myblog-2021-3bfc5-default-rtdb.firebaseio.com/posts.json')
      .then(function (data) {
        return data.json()
        // console.log(data.json())
        // this.blogs = data.body.slice(0, 10)
        // console.log(this.blogs)
      })
      .then(function (data) {
        // eslint-disable-next-line no-unused-vars
        const blogsArr = []
        for (let key in data) {
          // console.log(key)
          // console.log(data[key])
          data[key].id = key
          blogsArr.push(data[key])
        }
        // console.log(blogsArr)
        this.blogs = blogsArr
        console.log(this.blogs)
      })
  },
  computed: {
    filteredBlogs: function () {
      return this.blogs.filter((blog) => {
        return blog.title.match(this.search)
      })
    }
  },
  filters: {
    'to-upperCase': function (value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style>
#show-blogs{
  max-width: 960px;
  margin:0 auto;
}
#show-blogs h1{
  color: indianred;
}
.single-blog{
  padding: 20px;
  margin: 20px 0;
  box-sizing: border-box;
  background: #FAFAFA;
  border: 1px dotted #aaaaaa;
}
.single-blog a:link{
  color: black;
  text-decoration: none;
}
.single-blog a:visited{
  color: #aaaaaa;
  text-decoration: none;
}
input{
  padding: 10px;
  width: 100%;
  box-sizing: border-box;
}
</style>
