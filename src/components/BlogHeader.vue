<template>
  <div>
    <ul>
      <li>
        <router-link to="/" exact>博客总览</router-link>
        <router-link to="/add" exact>写个博客</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'blog-header'
}
</script>

<style scoped>
ul{
  list-style-type: none;
  text-align: center;
  margin: 0;
}
li{
  display: inline-block;
  margin: 0 10px;
}
a{
  color: ghostwhite;
  text-decoration: none;
  padding: 12px;
  border-radius: 5px;
}
div{
  background: indianred;
  padding: 30px 0;
  margin-bottom: 40px;
}
.router-link-active{
  background: darkred;
  color: white;
}
</style>
