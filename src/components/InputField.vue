<template>
  <form>
    <input v-model="userQuery"/>
    <button @click.prevent="submitHandler">Submit Query</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
  value: String,
});

console.log(props.value);

const userQuery = ref('');

function submitHandler(e) {
  console.log(e);
  console.log('this works!');
  console.log(props);
}
</script>
