<template>
  <div>
    <div class="container">
      <div>
        <h1 class="title">
          Sensors
        </h1>
      </div>
    </div>

    <div class="container">
      <DataTable 
        :items="sensors" 
        @click="logIt(sensor.messageAlerte + sensor.id)" 
      />
    </div>

  </div>
</template>

    

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>

<script>
import DataTable from "@/components/DataTable"; 

export default {
  components: {
    DataTable,
  },
  data () {
    return {
      sensors :[
        {
          "idApp": 45454,
          "date": "2020-01-01",
          "type": "typetest",
          "valeur": "valeurtest",
          "alerte": false,
          "messageAlerte": "message test"
        },
        {
          "idApp": 66666,
          "date": "2020-01-01",
          "type": "Ceci est un type",
          "valeur": "Ceci est une valeur",
          "alerte": false,
          "messageAlerte": "Alerte de message"
        },
        {
          "idApp": 127891,
          "date": "2020-01-06",
          "type": "le type",
          "valeur": "la valeur du senseur",
          "alerte": false,
          "messageAlerte": "ALARME"
        }   
      ] 
    }
  },
  methods:{
    logIt: function(name){
      console.log(name);
    }
  },
  beforeMount() {
      this.username = localStorage.getItem("username") || "USERNAMENOTFOUND404"
      this.token = localStorage.getItem("token") || this.$router.push('login');   
  }
}

  /*export default {
    data() {
      return {
        sensors: [
            {
            _id:"1",
            name: "patate1",
            msg: "une patate"
          },
          {
            _id:"32",
            name: "patate2",
            msg: "deux patates"
          }

        ]
      }
    },    
    async fetch() {
      const requestOptions = {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify( [
          {
            _id:"1",
            name: "patate1",
            message: "une patate"
          },
          {
            _id:"32",
            name: "patate2",
            message: "deux patates"
          }
        ] )
      };
      fetch("https://jsonplaceholder.typicode.com/posts", requestOptions)
      .await(response => response.json())
      .then(data => (this.sensors = data));
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
*/
</script>

formdata = 

  {
    request: "bla",
    limit: "blabl;a"
  }


GET /sensors/ {limit, offset}

GET /sensor/id {limit, offset}

GET /alerts {limit, offset}

GET /sensor/id/alerts {limit, offset}
