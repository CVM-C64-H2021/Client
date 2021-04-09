<template>
  <p v-if="$fetchState.pending">Fetching mountains...</p>
  <p v-else-if="$fetchState.error">An error occurred :(</p>
  <div v-else>
    <h1>Nuxt Mountains</h1>
    <ul>
      <li v-for="mountain of mountains">{{ mountain.title }}</li>
    </ul>
    <button @click="$fetch">Refresh</button>  
    <button v-on:click="say('what')">Say what</button>  
    <button v-on:click="fetch2()">Fetch2</button>  
    
  </div>
</template>

<script>
  export default {
    data() {
      return {
        mountains: []
      }
    },    
    async fetch() {
      const requestOptions = {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ title: "Vue POST Request Example" })
  };
    fetch("https://jsonplaceholder.typicode.com/posts", requestOptions)
    .then(response => response.json())
    .then(data => (this.mountains[0] = data));
    },
    methods: {
      say: function (message) {
        alert(message)
    },
    async fetch2() {
      this.mountains = await fetch(
        'https://api.nuxtjs.dev/mountains'
      ).then(res => res.json())
    }
    }
  }
</script>