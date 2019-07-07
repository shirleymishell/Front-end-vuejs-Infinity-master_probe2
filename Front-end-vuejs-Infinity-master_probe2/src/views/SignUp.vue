<template> 

    <div class="container">
      <br>
    
      <br>
      
            <h2 id="nombre2">Registrate</h2>
        <img alt="Vue logo" src="../assets/registro.png">
        <form action="" method="POST" @submit.prevent="register">

            <br>
            <div class="form-group" id="casilla2">
                <input class="form-control" type="user" v-model="user" name="user" id="user" placeholder="Username" required>
            </div>

            <div class="form-group" id="casilla2">
                <input class="form-control" type="email" v-model="email" name="email" id="email" placeholder="Email" required>
            </div>
            <div class="form-group" id="casilla2">
                <input class="form-control" type="password" v-model="password"  name="password" id="password" placeholder="Password" required>
            </div>

      <br><br> 
            <div class="form-group">
                <button type="submit" class="btn btn-success" id="boton2">Registro </button>

            </div>
        </form>
 
    </div> 
</template>

<script >
import gql from  'graphql-tag'
import { onRegister} from '../vue-apollo'

export default {
    data () {
        return {
            email : '',
            password : '',
            user : ''
        }
    },
    methods: {
        register() {
            this.$apollo.mutate({
            // Query
            mutation: gql`mutation ($input: SignUpInput! ) {
                signUp (input : $input) {
                    token
                }
            }`,
            // Parameters
            variables: {
                input : {
                    user: this.user,
                    email : this.email,
                    password : this.password
                }  
            },
            }).then((data) => {
            // Result
            console.log(data)
            //onRegister(this.$apollo.provider.defaultClient, data.data.register.token)
            this.$router.push('./Index.vue')
            }).catch((error) => {
            console.error(error)
            
            })
        },
},

}
</script>

<style>
#nombre2 {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
   text-shadow: 3px 2px white;
 }

#boton2 {
   
  background-color: #1ee11e;  
  border: none;
  color: white;
  hight: 40px;
  width: 151px; 
  margin: 10px 12px;
  cursor: pointer;

 }  

#casilla2 {
 display: inline-block;
    text-align: left;
    width: 55%;
    vertical-align: bottom; 
 } 
 
 input:invalid {
  border: 2px solid red;
} 

  input:valid {
  border: 2px solid green;
}

</style>
