<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{error}}</div>
    <div v-if="posts.length">
      <PostList :posts="posts"></PostList>
    </div>
    <div v-else>
      Loading...
    </div>
  </div>
</template>

<script>
import getPosts from '../composobles/getPosts.js'
import PostList from '../components/PostList.vue'

export default {
  name: 'HomeView',
  components: {
    PostList
  },
  setup(){
    const { posts, error, load } = getPosts();
    load();

    return {posts, error};
  }
}
</script>
