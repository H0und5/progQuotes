<template>
  <InputField @query-test.prevent="handleQuery"/>
</template>

<script setup>
import InputField from './components/InputField.vue';

const handleQuery = (query) => {
  console.log(query);
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
