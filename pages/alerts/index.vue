<template>
  <div class="container">
    <div id="app">
      <h1 class="font-titre">Alerts</h1>

      <hr />

      <h5>Alertes en vigueur</h5>
      <label class="select-box couleur-accent">Nombre de résultats par page: </label>
      <select class="select-box" @change="setSelected($event)">
        <option></option>
        <option value="10">10</option>
        <option value="25">25</option>
        <option value="50">50</option>
      </select>
      <DataTable :items="items" @onItemSelected="onItemSelected" />
      <hr />
      <Pagination
        :limit="limit"
        :offset="offset" @updateOffset="updateOffset"

      />
    </div>
  </div>
</template>

<script>
import DataTable from "@/components/DataTable";
import Pagination from "@/components/Pagination";

export default {
  components: {
    DataTable,
    Pagination,
  },
  data() {
    return {
      offset: 0,
      limit: 10,
      items: [],
      error: null
    };
  },
  computed: {
    itemCount() {
      console.log("THIS.ITEMS.LENGTH " + this.items.length);
      if(this.items && this.items.length > 0) {
        return this.items.length;
      }
    },
  },
  mounted() {
      this.username = localStorage.getItem("username") || "USERNAMENOTFOUND404";
      this.token = localStorage.getItem("token") || this.$router.push("login");
      this.getData()
    },
  methods: {
    async getData (){
      let formdata = {
          method : "GET",
          headers : {
            'Content-Type' : 'application/json',
            'authorization' : localStorage.getItem("token")
            
          }
        }

      try{
        const response = await fetch("https://c64.herokuapp.com/api/alerts/?limit="+this.limit+"&offset="+this.offset, formdata);
        const data = await response.json();
        this.items = data;
      }
      catch(error){
        console.log(error);
      }
    },
    onItemSelected(item) {
      alert(item);
    },
    updateOffset(newOffset) {

      this.offset = newOffset;
      console.log(this.offset);
      this.getData();

    },
    setSelected(event) {
      var optionValue = event.target.value;
      this.limit = parseInt(optionValue);
    },
  },
  beforeMount(){
      this.token = localStorage.getItem("token") || this.$router.push('login');       
    },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
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
