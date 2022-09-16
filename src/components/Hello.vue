<script lang="ts" setup>
  import axios from "axios";
  import { reactive } from "vue";
  const props = defineProps<{ msg: string }>();

  const data = reactive({
    jsonPlaceHolder: null,
  });
  function handleClick() {
    console.log("clicked");
    axios
      .get("https://jsonplaceholder.typicode.com/todos/")
      .then((response) => {
        console.log(response);
        data.jsonPlaceHolder = response.data;
        console.log(data.jsonPlaceHolder);
      })
      .catch((error) => {
        console.log(error);
      });
  }
</script>

<template>
  <h3>{{ msg }}</h3>
  <button @click="handleClick">{{ msg }}</button>
  <p>
    Hello
    {{ data.jsonPlaceHolder }}
  </p>
  <p>
    Recommended IDE setup:
    <a href="https://code.visualstudio.com/" target="_blank">VSCode</a>
    +
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
  </p>

  <p>
    See
    <code>README.md</code> for more information.
  </p>

  <p>
    <a href="https://vitejs.dev/guide/features.html" target="_blank"
      >Vite Docs</a
    >
    |
    <a href="https://v3.vuejs.org/" target="_blank">Vue 3 Docs</a>
  </p>
</template>

<style scoped>
  a {
    color: #42b983;
  }

  label {
    margin: 0 0.5em;
    font-weight: bold;
  }

  code {
    background-color: #eee;
    padding: 2px 4px;
    border-radius: 4px;
    color: #304455;
  }
</style>
