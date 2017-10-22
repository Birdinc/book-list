<template>
  <div id="app" class="container">
    <div class="page-header">
      <h1>David's Book List</h1>
    </div>
    <div class="panel panel-default">
      <div class="panel-heading">
        <h3 align="left">List</h3>
      </div>
      <div class="panel-body">
        <table class="table table-striped">
          <thead>
            <tr>
              <th>
                Title
              </th>
              <th>
                Author
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="book in books">
              <td>
                <a v-bind:href="book.url">{{book.title}}</a>
              </td>
              <td>
                {{book.author}}
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
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

let booksRef = db.ref('books');

export default {
  name: 'app',
  firebase: {
    books: booksRef
  }
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
