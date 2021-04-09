<template>
  <div class="container">
   <form action="">
        <label for="courriel">Courriel</label>
        <input name="courriel" type="text" placeholder="votre courriel ici">
        <label for="password">Password</label>
        <input name="password" type="password" placeholder="votre password ici">
        <button type="submit">Submit</button>
    </form>
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
        
export default {
    
}

let repAPI = 
{
  id: "id",
  date: "2020-04-09",
  type: "type",
  valeur: "valeur",
  alerte: "0 ou 1",
  messageAlerte: "msg ici"
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
