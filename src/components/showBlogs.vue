<template>
  <div id="showBlogs">
    <h1>All articles</h1>
    <div v-for="(post, index) in posts" :key="index" class="single-blog">
      <h2>{{ post.title}}</h2>
      <p>{{ post.body }}</p>

      <hr v-if="posts.length-1">
    </div>
  </div>
</template>

<script>
 export default {
   data: () => {
     return {
       posts: []
     }
   },
   mounted(){
     this.$http.get('https://jsonplaceholder.typicode.com/posts').then((data) => {
       this.posts = data.body.slice(0,10);
     })
   }
  }
</script>

<style lang="scss" scoped>
  #showBlogs{
    max-width: 800px;
    margin: 0 auto;
    h1 {
        text-align: center;
      }
    .single-blog{

      

      h2, p {
        text-transform: lowercase;
      }
    }
  }
</style>