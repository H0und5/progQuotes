<template>
  <form @submit.prevent="submitHandler">
    <input placeholder="Enter a number" v-model="numberReq" />
    <button>Submit number</button>
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
