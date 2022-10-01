<template>
  <h1>Programmer Quotes</h1>
  <InputField @number-requested="updateQuery"/>
  {{ output }}
</template>

<script setup>
import { ref } from 'vue';
import InputField from './components/InputField.vue';

const baseURL = 'https://programming-quotes-api.herokuapp.com/Quotes?count=';

const output = ref();

const handleQuery = async () => {
  const res = await fetch(`${baseURL}${output.value}`);

  if (!res.ok) {
    throw new Error();
  }

  const data = await res.json();

  console.log(res);

  console.log(data);
};

const updateQuery = (query) => {
  console.log(query);
  output.value = query;

  handleQuery();
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
