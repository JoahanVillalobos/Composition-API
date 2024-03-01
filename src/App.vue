<script setup>
import { ref, computed } from 'vue'

import BlogPost from './components/BlogPost.vue'
import PaginatePost from './components/PaginatePost.vue';

const posts = ref([])
const favorito = ref('')
const pageXpost = 10
const inicio = ref(0)
const fin = ref(pageXpost)

const top = computed(() => posts.value.length)


const cambiarFavorito = (title) => {
  favorito.value = title
}

const next = () => {
  inicio.value += pageXpost
  fin.value += pageXpost
}
const previous = () => {
  inicio.value -= pageXpost
  fin.value -= pageXpost
}


// LLamar al API
fetch('https://jsonplaceholder.typicode.com/posts')
  .then((res) => res.json())
  .then((data) => posts.value = data)


</script>

<template>
  <div class="container">
    <h1>APP</h1>
    <h2>Mi Post Favorito: {{ favorito }}</h2>

    <PaginatePost class="mb-2" :inicio='inicio' :fin='fin' :top="top" @next="next" @previous="previous" />

    <BlogPost v-for="post in posts.slice(inicio, fin)" :key="post.id" :title="post.title" :id="post.id"
      :body="post.body" @cambiarFavorito="cambiarFavorito" class="mb-2" />
  </div>
</template>
