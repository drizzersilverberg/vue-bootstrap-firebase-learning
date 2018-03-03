<template>
  <div id="app">
    <div v-for="message in messages">
      <h4>{{ message.title }}</h4>
      <p>{{ message.text }}</p>
      <p>{{ message.timestamp }}</p>
    </div>
  </div>
</template>

<script>
  import Firebase from 'firebase'

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
