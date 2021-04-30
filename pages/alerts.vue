<template>
  <div class="container">
    <div>
      <h1 class="font-titre">Alerts</h1>

      <hr />

      <h5>Alertes en vigueur</h5>
      <DataTable :items="items" @onItemSelected="onItemSelected" />
      <hr />
    </div>
  </div>
</template>

<script>
import DataTable from "@/components/DataTable";

let patate = 3;

export default {
  components: {
    DataTable,
  },
  data() {
    return {
      items: [
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
          type: "type",
          valeur: "Valeur louche",
          alerte: "1",
          messageAlerte: "Ça va pô ben",
        },
      ],
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
  methods: {
    onItemSelected: function (item) {
      alert(item);
    },
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
