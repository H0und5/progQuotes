<template>
  <form @submit.prevent="submitHandler">
    <input v-model="userQuery"/>
    <button>Submit Query</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const userQuery = ref('');

const emit = defineEmits(['queryTest']);

function submitHandler() {
  console.log(userQuery);
  console.log('this works!');
  emit('queryTest', userQuery.value);
}
</script>
