<template>
<ul class="post-list">
  <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
</ul>
</template>

<script setup>
  import PostService from '@/services/PostService'
  import { onMounted } from 'vue'
  const  service = new PostService()
  const posts = service.getPosts()

  onMounted(async () => {
    await service.fetchAll()
  })
</script>

<style scoped lang="scss">
.post-list {
  width: 95vw;
  height: 75px;
  padding: 20px;
  list-style-type: none;

  li {
  padding: 10px;
  width: 100%;
  border: 1px solid #ccc;
  color: $red ;
  }

  li:hover {
    background-color: darken($color: #0c0c0c, $amount: 1%)
  }
}
</style>
