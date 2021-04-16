<template>
  <div class="container">
    <div>
      <h1 class="font-titre">
        Alerts
      </h1>

      

      <hr>

            <h5>Alertes en vigueur</h5>

            <table>

                <tr>
                    <th>Sensor id</th>
                    <th>Date</th>
                    <th>Type</th>
                    <th>Valeur</th>
                    <th>Message</th>
                </tr>
                <tr v-for="alert in alerts" :key="alert.id">
                    <td>{{ alert.id }}</td>
                    <td>{{ alert.date }}</td>
                    <td>{{ alert.type }}</td>
                    <td>{{ alert.valeur }}</td>
                    <td>{{ alert.messageAlerte }}</td>
                </tr>

            </table>

            <hr>

    </div>
  </div>
</template>

<script>

let patate = 3

export default {
    data() {
      return {
        alerts: []
      }
    },    
    async fetch() {
      const requestOptions = {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify( [
   {
      id:"1",
      date:"2020-04-09",
      type:"type",
      valeur:"valeur",
      messageAlerte:"Allô"
   },
   {
      id:"32",
      date:"2020-04-09",
      type:"type",
      valeur:"Valeur louche",
      messageAlerte:"Ça va pô ben"
   }
] )
  };
    fetch("https://jsonplaceholder.typicode.com/posts", requestOptions)
    .then(response => response.json())
    .then(data => (this.alerts = data));
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

let repAPI = [
   {
      id:"id",
      date:"2020-04-09",
      type:"type",
      valeur:"valeur",
      messageAlerte:"msg ici"
   },
   {
      id:"id",
      date:"2020-04-09",
      type:"type",
      valeur:"valeur",
      messageAlerte:"msg ici"
   }
]








</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
  'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  letter-spacing: 1px;
}
.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
}
.links {
  padding-top: 15px;
}
</style>
