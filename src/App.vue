<template>
  <h1>Programmer Quotes</h1>
  <InputField @number-requested="updateQuery" />
  <div v-for="quote in queryOutput" :key="quote.id">
    <p>{{quote.en}}</p>
    <button @click.prevent="deleteQuote(quote.id)">Delete this quote</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import InputField from './components/InputField.vue';

const baseURL = 'https://programming-quotes-api.herokuapp.com/Quotes?count=';

const userInput = ref();
const queryOutput = ref();

// const handleQuery = async () => {
//   const res = await fetch(`${baseURL}${userInput.value}`);

//   if (!res.ok) {
//     throw new Error();
//   }

//   const data = await res.json();

//   queryOutput.value = data;

//   console.log(queryOutput.value);
// };

const hello = () => {
  fetch(`${baseURL}${userInput.value}`)
    .then((response) => {
      if (!response.ok) {
        throw new Error();
      } else {
        return response.json();
      }
    })
    .then((data) => {
      queryOutput.value = data;
    })
    .catch((error) => console.log(error));
};

const updateQuery = (query) => {
  console.log(query);
  userInput.value = query;

  hello();
};

const deleteQuote = (id) => {
  console.log(id);
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
