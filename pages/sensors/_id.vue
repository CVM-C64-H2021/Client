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
      <hr />
      <Pagination
        :limit="limit"
        :offset="offset" @updateOffset="updateOffset"

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
import Pagination from "@/components/Pagination";

export default {
  components: {
    DataTable,
    Pagination,
  },
  data () {
    return {
      limit: 10,
      offset : 0,
      sensors :[
    
      ] 
    }
  },
  methods:{
    logIt: function(name){
      console.log(name);
    },
    updateOffset(newOffset) {

      this.offset = newOffset;
      console.log(this.offset);
      this.getData();

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
        const id = this.$route.params.id;
        console.log("ID"+ id);
        const response = await fetch("https://c64.herokuapp.com/api/sensor/"+id+"?limit="+this.limit+"&offset="+this.offset, formdata);
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
 
