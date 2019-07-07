<template>
    <div class="container">
     
      <br><br>
<br>
        <h2 id="f1">Iniciar Sesión</h2>
            <img alt="Vue logo" src="../assets/login.png">
        <form action="" method="POST" @submit.prevent="login">
        <br>
            
            <br>

            <div class="form-group" id="casilla">
                <input class="form-control" type="email" v-model="email" name="email" id="email" placeholder="Email"  required>
            </div>
            <div class="form-group" id="casilla">
                <input class="form-control" type="password" v-model="password"  name="password" id="password" placeholder="Password"  required>
            </div> 
            <div class="form-group">
                <button type="submit" class="btn btn-primary" id="boton" >Login</button>
                <br><br>
            </div>

        </form>

    </div> 
</template>

<script>
import gql from  'graphql-tag'
import { onLogin } from '../vue-apollo'

export default {
    data () {
        return {
            email : '',
            password : ''
        }
    },
    methods: {
        login() {
            this.$apollo.mutate({
            // Query
            mutation: gql`mutation ($input: SignInInput! ) {
                signIn (input : $input) {
                    token
                }
            }`,
            // Parameters
            variables: {
                input : {
                    email : this.email,
                    password : this.password
                }  
            },
            }).then((data) => {
            // Result
            console.log(data)
            //onLogin(this.$apollo.provider.defaultClient, data.data.login.token)
            this.$router.push('./Index.vue')
            }).catch((error) => {
            console.error(error)
            
            })
        },
},
}
</script>


<style>
#f1 {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
   text-shadow: 3px 2px white;
 } 

#boton {
   
  background-color: #EABE3F;  
  border: none;
  color: white;
  hight: 40px;
  width: 151px; 
  margin: 10px 12px;
  cursor: pointer;

 } 
#casilla {
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
