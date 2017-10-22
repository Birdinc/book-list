<template>
  <div id="app">

  </div>
</template>

<script>

import Firebase from 'firebase'

let config = {
  apiKey: "AIzaSyBR6B9BMS2xkTIJzS_saoZncy4mgfJnBeM",
  authDomain: "booklist-5f201.firebaseapp.com",
  databaseURL: "https://booklist-5f201.firebaseio.com",
  projectId: "booklist-5f201",
  storageBucket: "booklist-5f201.appspot.com",
  messagingSenderId: "122948188584"
}

// establish connection to firebase
let app = Firebase.initializeApp(config);
let db = app.database();

let bookRef = db.ref('books');

export default {
  name: 'app'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
