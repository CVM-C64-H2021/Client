<template>
  <div class="container">

   <form v-on:submit.prevent action="">
        <label for="username">Username</label>
        <input name="username" type="text" v-model="username" placeholder="votre nom d'utilisateur ici">
        <label for="password">Password</label>
        <input name="password" type="password" v-model="password" placeholder="votre password ici">
        <button v-on:click="signin()"  type="submit">Submit</button>

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
        
export default {  
  
    data() {
      return {
        msg: "Pataaaaate",   
        password: "AAAaaa111",
        username: "test1234"
      }
    },
    methods: {      
    async signin () {
        
        localStorage.setItem('username', this.username)
        try {
          let requestoptions = {
              method: "POST",
              body: JSON.stringify({
                  "username": this.username,
                  "password": this.password,
              }),
              headers: {
                  'Content-Type': 'application/json'
              }
          }       
          
          const response = await fetch("https://c64.herokuapp.com/api/login/", requestoptions);
            const data = await response.json()
          
          if(response.status == 400){            
            console.log(data.Error);
          }
          else if(response.status == 200){
            console.log(data.token);
            localStorage.setItem('token', data.token)
            this.$router.push('lobby');
          }
        } catch (error) {
          if(response.status == 400){            
            console.log("Erreur");
          }
          console.log("erreur dans le fetch");
        }
          
   

      
       
        
       
            

        return false;
    }   
    }
  }

    
    


let repAPI = [
  {
  id: "id",
  date: "2020-04-09",
  type: "type",
  valeur: "valeur",
  alerte: "0 ou 1",
  messageAlerte: "msg ici"
},
  {
  id: "id",
  date: "2020-04-09",
  type: "type",
  valeur: "valeur",
  alerte: "0 ou 1",
  messageAlerte: "msg ici"
},
  {
  id: "id",
  date: "2020-04-09",
  type: "type",
  valeur: "valeur",
  alerte: "0 ou 1",
  messageAlerte: "msg ici"
},
  {
  id: "id",
  date: "2020-04-09",
  type: "type",
  valeur: "valeur",
  alerte: "0 ou 1",
  messageAlerte: "msg ici"
}

]

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
