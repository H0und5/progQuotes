<!-- eslint-disable vuejs-accessibility/label-has-for -->

<template>
  <form @submit.prevent="handleNewQuote(newQuote, newAuthor)">
    <label>New Quote</label>
    <textarea placeholder="Enter your quote here." v-model="newQuote" />

    <br />

    <label>New Author</label>
    <input placeholder="Enter the author here." v-model="newAuthor" />

    <button>Submit Quote</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const emit = defineEmits(['submitQuote']);

const newQuote = ref('');
const newAuthor = ref('');

const handleNewQuote = () => {
  const newId = Math.floor(Math.random() * 10000000000);

  console.log(newId);

  const quoteAndAuthor = {
    id: `${newId}`,
    en: `${newQuote.value}`,
    author: `${newAuthor.value}`,
  };

  console.log(`This got passed first: + ${newQuote.value} + ${newAuthor.value}`);
  emit('submitQuote', quoteAndAuthor);
};

</script>
