<template>
  <form @submit.prevent="submitHandler">
    <input v-model="numberReq"/>
    <button>Submit Query</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const numberReq = ref('');

const emit = defineEmits(['numberRequested', '']);

function submitHandler() {
  console.log('this works!');
  emit('numberRequested', numberReq.value);
}
</script>
