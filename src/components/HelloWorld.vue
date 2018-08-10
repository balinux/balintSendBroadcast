<template>
  <div class="container">
  <nav class="nav justify-content-center|justify-content-end">
  <a class="nav-link active" href="https://linebotnodejsbalinux.herokuapp.com"> home</a>
</nav>
    <form>
    <div class="jumbotron">
      <h1 class="display-3">Balint Broadcast</h1>
      <hr class="my-2">
            <div class="form-group">
        <label for="exampleInputEmail1">kirim broadcast</label>
        <input v-model="dataBroadcast" type="text" class="form-control"  placeholder="Masukkan pesan broadcast">
      </div>
      <button type="submit" @click="sendBroadcast" class="btn btn-primary">Submit</button>

    </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HelloWorld",
  data() {
    return {
        msg: "Welcome to Your Vue.js App",
        dataBroadcast:""
    };
  },
  created() { 
    axios.get('https://linebotnodejsbalinux.herokuapp.com/broadcast/balinux') 
      .then((data) => {
        console.log(data)
        }).catch((error) => {
        console.log(error)
      })
  },
  methods:{
    sendBroadcast(){
      console.log("sending message to broadcast")
    // axios.get('https://api.chucknorris.io/jokes/random')
      axios.get(`https://linebotnodejsbalinux.herokuapp.com/broadcast/${this.dataBroadcast}`)
      .then((data) => {
        console.log(data)
        }).catch((error) => {
        console.log(error)
      })
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
