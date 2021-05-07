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
      limit: 10,
      offset : 0,
      sensors :[
        /*{
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
        }*/   
      ] 
    }
  },
  methods:{
    logIt: function(name){
      console.log(name);
    },
    async getData (){
      let formdata = {
          method : "GET",
          headers : {
            'Content-Type' : 'application/json',
            'authorization' : localStorage.getItem("token")
            
          }
        }

      try{
        const response = await fetch("https://c64.herokuapp.com/api/sensors/", formdata);
        const data = await response.json();
        this.sensors = data;
      }
      catch(error){
        console.log(error);
      }
    }

  },
  beforeMount(){
      this.token = localStorage.getItem("token") || this.$router.push('login');       
    },
    mounted() {
      this.username = localStorage.getItem("username") || "USERNAMENOTFOUND404";
      this.getData();
    }  
}
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
