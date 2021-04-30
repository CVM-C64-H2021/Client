<template>
  <p v-if="$fetchState.pending">Fetching mountains...</p>
  <p v-else-if="$fetchState.error">An error occurred :(</p>
  <div v-else>
    <h1>Nuxt test</h1>
    <ul>
      <li v-for="mountain of mountains">{{ mountain.status }}</li>
    </ul>
    <button v-on:click="say('what')">Say what</button>  
    <button v-on:click="fetch2()">{{username}}</button>  
    
  </div>
</template>

<script>
  export default {
    data: function() {
  	return {
    	mountains: [{
        status : "Ceci n'est pas un test"
      }],
      username: "Henri"
      }
    
  },
  mounted() {
      this.username = localStorage.getItem("username") || "USERNAMENOTFOUND404"
},
  async fetch() {
      this.mountains = await fetch(
        'https://postman-echo.com/get?test=123'
      ).then(res => res.json())
    },
    methods: {
      say: function (message) {
        alert(message)
    },
    async fetch2() {
      this.mountains = [{
        status : "Ceci est un test"
      }]
    }
    }
    
  }
</script>