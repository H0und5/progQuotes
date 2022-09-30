<template>
  <form>
    <input v-model="test"/>
    <button @click.prevent="submitHandler">Submit Query</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const test = ref('');

function submitHandler(e) {
  console.log(e);
}
</script>
