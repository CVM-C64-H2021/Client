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
      <table id="laTable">
        <thead>
          <tr>
            <th>Sensor</th>
            <th>name</th>
            <th>data</th>
          </tr>
        </thead>
          
        <tbody>
          <tr v-for="sensor in sensors" :key="sensor._id">
            <td>{{sensor._id}}</td>
            <td>{{sensor.name}}</td>
            <td>{{sensor.msg}}</td>
          </tr>
        </tbody>
      </table>
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
    console.log("patate");
    let patate = 3
  export default {
    data () {
      return {
        sensors :[
          {_id: "0001", name: "patate1", msg: "une Patate"},
          {_id: "0002", name: "patate2", msg: "deux Patates"},
          {_id: "0003", name: "patate3", msg: "trois Patates"} 
        ]
      }
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
