<template>
  <div id="app">
    <h1>{{ message }}</h1>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      message: ''
    };
  },
  created() {
    axios.get('http://localhost:8000/api')
      .then(response => {
        this.message = response.data.Hello;
      })
      .catch(error => {
        console.error('Fehler beim Abrufen der Daten:', error);
      });
  }
};
</script>

<style>
/* Optionales CSS */
</style>
