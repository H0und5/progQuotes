<template>
  <form>
    <input v-model="userQuery"/>
    <button @click.prevent="submitHandler">Submit Query</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const userQuery = ref('');

const emit = defineEmits(['queryTest']);

function submitHandler(e) {
  console.log(e);
  console.log('this works!');
  emit('queryTest', e);
}
</script>
