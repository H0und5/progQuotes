<!-- eslint-disable vuejs-accessibility/label-has-for -->
<template>
  <InputTest @submit-quote="addQuote"/>

  <h1>Programmer Quotes</h1>
  <InputField @number-requested="updateQuery" />
  <div v-for="quote in currentOutput" :key="quote.id">
    <p>{{quote.en}}</p>
    <label for="update"></label>
    <textarea v-if="editStatus" v-model="quote.en" id="update"/>
    <button v-if="!editStatus" @click.prevent="editQuote(quote.id, quote.en)">
      Edit this quote
    </button>
    <button v-if="editStatus" @click.prevent="submitEditQuote(quote.id, quote.en)">
      Finish Editing Quote
    </button>
    <button @click.prevent="deleteQuote(quote.id)">
      Delete this quote
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import InputField from './components/InputField.vue';
import InputTest from './components/InputTest.vue';

const baseURL = 'https://programming-quotes-api.herokuapp.com/Quotes?count=';

const userInput = ref();
const currentOutput = ref();
const editStatus = ref(false);

// const handleQuery = async () => {
//   const res = await fetch(`${baseURL}${userInput.value}`);

//   if (!res.ok) {
//     throw new Error();
//   }

//   const data = await res.json();

//   currentOutput.value = data;

//   console.log(currentOutput.value);
// };

// Get Quotes
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
      const newData = Object.assign(data);

      console.log(newData);

      currentOutput.value = data;
    })
    .catch((error) => console.log(error));
};

// Get # of quotes from user
const updateQuery = (query) => {
  console.log(query);
  userInput.value = query;

  hello();
};

// Delete a Quote
const deleteQuote = (id) => {
  const nextCurrentQuery = currentOutput.value.filter((query) => query.id !== id);

  console.log(nextCurrentQuery);

  currentOutput.value = nextCurrentQuery;
};

// Edit a quote
const editQuote = (id, en) => {
  console.log(id, en);

  editStatus.value = !editStatus.value;
};

const submitEditQuote = (id, en) => {
  console.log(id, en);

  console.log(currentOutput);

  editStatus.value = !editStatus.value;
};

// Add a quote
const addQuote = (quoteAndAuthor) => {
  console.log(quoteAndAuthor, currentOutput);

  // const newAdd = { quoteAndAuthor };
  //
  const currentPosition = currentOutput.value.length;

  currentOutput.value[`${currentPosition}`] = quoteAndAuthor;

  // currentOutput.value = { ...currentOutput.value, newAdd };

  console.log(typeof currentOutput.value, currentOutput, currentOutput);
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
