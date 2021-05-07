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
        :totalPages="totalPages"
        :totalItems="totalItems"
        :itemsPerPage="itemsPerPage"
        :currentPage="currentPage"
        @onPageChanged="onPageChanged"
      />
    </div>
  </div>
</template>

<script>
import DataTable from "@/components/DataTable";
import Pagination from "@/components/Pagination";

let patate = 3;

export default {
  components: {
    DataTable,
    Pagination,
  },
  data() {
    return {
      items: [
        {
          idApp: "1",
          date: "2020-04-09",
          type: "type",
          valeur: "valeur",
          alerte: "1",
          messageAlerte: "Allô",
        },
        {
          idApp: "32",
          date: "2020-04-09",
          type: "type",
          valeur: "Valeur louche",
          alerte: "1",
          messageAlerte: "Ça va pô ben",
        },
        {
          idApp: "1",
          date: "2020-04-09",
          type: "type",
          valeur: "valeur",
          alerte: "1",
          messageAlerte: "Allô",
        },
        {
          idApp: "32",
          date: "2020-04-09",
          type: "type2",
          valeur: "Valeur louche",
          alerte: "1",
          messageAlerte: "Ça va pô ben",
        },
        {
          idApp: "1",
          date: "2020-04-09",
          type: "type",
          valeur: "valeur",
          alerte: "1",
          messageAlerte: "Allô",
        },
        {
          idApp: "32",
          date: "2020-04-09",
          type: "type2",
          valeur: "Valeur louche",
          alerte: "1",
          messageAlerte: "Ça va pô ben",
        },
        {
          idApp: "1",
          date: "2020-04-09",
          type: "type",
          valeur: "valeur",
          alerte: "1",
          messageAlerte: "Allô",
        },
        {
          idApp: "32",
          date: "2020-04-09",
          type: "type2",
          valeur: "Valeur louche",
          alerte: "1",
          messageAlerte: "Ça va pô ben",
        },
        {
          idApp: "1",
          date: "2020-04-09",
          type: "type",
          valeur: "valeur",
          alerte: "1",
          messageAlerte: "Allô",
        },
        {
          idApp: "32",
          date: "2020-04-09",
          type: "type2",
          valeur: "Valeur louche",
          alerte: "1",
          messageAlerte: "Ça va pô ben",
        },
        {
          idApp: "1",
          date: "2020-04-09",
          type: "type",
          valeur: "valeur",
          alerte: "1",
          messageAlerte: "Allô",
        },
        {
          idApp: "32",
          date: "2020-04-09",
          type: "type2",
          valeur: "Valeur louche",
          alerte: "1",
          messageAlerte: "Ça va pô ben",
        },
      ],
      currentPage: 1,
      itemsPerPage: 0,
      error: null

    };
  },
  async fetch() {
    const requestOptions = {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify([
        {
          id: "1",
          date: "2020-04-09",
          type: "type",
          valeur: "valeur",
          alerte: "1",
          messageAlerte: "Allô",
        },
        {
          id: "32",
          date: "2020-04-09",
          type: "type2",
          valeur: "Valeur louche",
          alerte: "1",
          messageAlerte: "Ça va pô ben",
        },
      ]),
    };
  },
  computed: {
    totalItems() {
      console.log("THIS.ITEMS.LENGTH " + this.items.length);
      if(this.items && this.items.length > 0) {
        return this.items.length;
      }
    },
    totalPages() {
      if(this.items && this.items.length > 0) {
        var limit = this.itemsPerPage > 0 ? this.itemsPerPage : 10;
        return Math.ceil(this.items.length / limit);
      }
      else {
        return 0;
      }
    },
  },
  methods: {
    onItemSelected(item) {
      alert(item);
    },
    mounted() {
      this.username = localStorage.getItem("username") || "USERNAMENOTFOUND404";
      this.token = localStorage.getItem("token") || this.$router.push("login");
    },
    onPageChanged(page) {
        this.currentPage = page;
    },
    setSelected(event) {
      var optionValue = event.target.value;
      this.itemsPerPage = parseInt(optionValue);
      console.log("ITEMS PER PAGE" + this.itemsPerPage);
    },
    totalPages() {
      if(this.totalItems < this.itemsPerPage) {

        this.totalPages = Math.Ceil(this.totalItems / this.itemsPerPage);
      }
      else {
        this.totalPages = 1;
      }

      console.log("TOTAL PAGES" + this.totalPages);
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
