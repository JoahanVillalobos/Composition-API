<script setup>
import { ref } from 'vue'
import BlogPost from './components/BlogPost.vue'
const posts = ref([
  { title: "Post 1", id: 1, body: "Descripción 1" },
  { title: "Post 2", id: 2, body: "Descripción 2" },
  { title: "Post 3", id: 3, body: "Descripción 3" },
  { title: "Post 4", id: 4 },
])

</script>

<template>
  <div class="container">
    <h1>APP</h1>
    <BlogPost v-for="post in posts" :key="post.id" :title="post.title" :id="post.id" :body="post.body" />
  </div>
</template>

