<template>
<div id="app" class="container">

  <div class="page-header">
    <h1>David's Book List</h1>
  </div>

  <div class="panel panel-default">
    <div class="panel-heading">
      <h3 align="left">Add Book</h3>
    </div>
    <div class="panel-body">
      <form id="form" class="form-inline" v-on:submit.prevent="addBook">
        <div class="form-group">
          <label for="bookTitle">Title</label>
          <input type="text" id="bookTitle" class="form-control" v-model="newBook.title">
        </div>
        <div class="form-group">
          <label for="bookAuthor">Author</label>
          <input type="text" id="bookTitle" class="form-control" v-model="newBook.author">
        </div>
        <div class="form-group">
          <label for="bookUrl">Url</label>
          <input type="text" id="bookTitle" class="form-control" v-model="newBook.url">
        </div>
        <input type="submit" class="btn btn-primary" value="Add Book">
      </form>
    </div>
  </div>

  <div class="panel panel-default">
    <div class="panel-heading">
      <h3 align="left">List</h3>
    </div>
    <div class="panel-body">
      <table class="table table-striped">
        <thead>
          <tr>
            <th>Title</th>
            <th>Author</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="book in books">
            <td><a v-bind:href="book.url" target="_blank">{{book.title}}</a></td>
            <td>{{book.author}}</td>
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
  },
  data () {
    return {
      newBook: {
        title: '',
        author: '',
        url: ''
      }
    }
  },
  methods: {
    addBook: function(){
        booksRef.push(this.newBook);
        this.newBook.title = '';
        this.newBook.author = '';
        this.newBook.url = '';
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 30px;
}
</style>
