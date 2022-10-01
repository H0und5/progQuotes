<template>
  <InputField @number-requested="handleQuery"/>
  {{ output }}
</template>

<script setup>
import { ref } from 'vue';
import InputField from './components/InputField.vue';

const output = ref();

const handleQuery = (query) => {
  console.log(query);
  output.value = query;
};

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
