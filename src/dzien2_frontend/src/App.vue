<script setup>
import { ref } from 'vue';
import { dzien2_backend } from 'declarations/dzien2_backend/index';
import Blog from './components/BLOG.vue';
let greeting = ref('');

async function handleSubmit(e) {
  e.preventDefault();
  const target = e.target;
  const name = target.querySelector('#name').value;
  await dzien2_backend.greet(name).then((response) => {
    greeting.value = response;
  });
}
</script>

<template>
  <main>
    <img src="/logo2.svg" alt="DFINITY logo" />
    <br />
    <br />
    <form action="#" @submit="handleSubmit">
      <label for="name">Enter your name: &nbsp;</label>
      <input id="name" alt="Name" type="text" />
      <button type="submit">Click Me!</button>
    </form>
    <section id="greeting">{{ greeting }}</section>
    <Blog />
  </main>
</template>
