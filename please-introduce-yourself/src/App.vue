<template>
  <div id="app" class="jumbotron">
    <div class="container">
      <h1>Hello! Nice to meet you!</h1>
      <hr/>
      <form action="#" @submit="addMessage">
        <div class="form-group">
          <input class="form-control" v-model="newMessage.title" maxlength="40" autofocus placeholder="Please introduce yourself :)" />
        </div> <!-- form-group -->
        <div class="form-group">
          <textarea class="form-control" v-model="newMessage.text" placeholder="Leave your message" rows="3"></textarea>
        </div> <!-- form-group -->
        <button class="btn btn-primary" type="submit">Send</button>
      </form>
      <hr/>
      <div class="card-group">
        <div class="card" v-for="message in messages">
          <div class="card-block">
            <h5 class="card-title">{{ message.title }}</h5>
            <p class="card-text">{{ message.text }}</p>
            <p class="card-text"><small class="text-muted">Added on {{ dateToString(message.timestamp) }}</small></p>
          </div> <!-- card-block -->
        </div> <!-- card -->
      </div> <!-- card-group -->
    </div> <!-- container -->
  </div> <!-- jumbotron -->
</template>

<script>
  import Firebase from 'firebase'
  import { dateToString } from './utils/utils'

  let config = {
    apiKey: "AIzaSyB68bmVWRGDNQp1zsFYlNmw9hl5taP958M",
    authDomain: "pleaseintroduceyourself-f17ca.firebaseapp.com",
    databaseURL: "https://pleaseintroduceyourself-f17ca.firebaseio.com",
    projectId: "pleaseintroduceyourself-f17ca",
    storageBucket: "pleaseintroduceyourself-f17ca.appspot.com",
    messagingSenderId: "199554124963"
  };

  let app = Firebase.initializeApp(config)
  let db = app.database()
  let messageRef = db.ref('messages')

  export default {
    name: 'app',
    firebase: {
      messages: messageRef
    },
    data () {
      return {
        newMessage: {
          title: '',
          text: '',
          timestamp: null
        }
      }
    },
    methods: {
      dateToString,
      addMessage (e) {
        // prevent page directing
        e.preventDefault()

        // prevent empty title and don't proceed
        if (this.newMessage.title === '') {
          return
        }

        // use current date
        this.newMessage.timestamp = Date.now()

        // save to firebase
        messageRef.push(this.newMessage)

        // clear form
        this.newMessage.title = ''
        this.newMessage.text = ''
        this.newMessage.timestamp = null
      },
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
