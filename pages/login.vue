<template>
  <div class="container">

   <form v-on:submit.prevent action="">
        <label for="username">Courriel</label>
        <input name="username" type="text" v-model="username" placeholder="votre courriel ici">
        <label for="password">Password</label>
        <input name="password" type="password" v-model="password" placeholder="votre password ici">
        <button v-on:click="signinDUMMY()"  type="submit">Submit</button>

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
        username: "",
        password: ""        
      }
    },
    methods: {
      signin: function () {
        
        localStorage["username"] = this.username
        console.log(this.username);
        fetch("https://jsonplaceholder.typicode.com/users", {
            method: "POST",
            credentials: 'include',
            body: JSON.stringify({
                "username": this.username,
                "password": this.password,
            }),
            headers: {
                'Content-Type': 'application/json'
            }
        })
            .then(response => response.json())
            .then(data => {
                if (data == "SIGNED_IN") {
                    this.$router.push('mountains');
                }
                else {
                    console.log("pas connecté");
                }
            });

        return false;
    },    
    async signinDUMMY () {
        
        localStorage.setItem('username', this.username)
        console.log(this.username);
        try {
          const response = await fetch("https://www.antoinechagnonmichaud.com/api/authenticate", {
            method: "POST",
            credentials: 'include',
            body: JSON.stringify({
                "username": this.username,
                "password": this.password,
            }),
            headers: {
                'Content-Type': 'application/json'
            }
            
        })
        const data = response.json()
        if (1 == 1) {            
              this.$router.push('lobby');
          }  
       
        } catch (error) {
          console.log(error);
          console.log("pas connecté");
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
