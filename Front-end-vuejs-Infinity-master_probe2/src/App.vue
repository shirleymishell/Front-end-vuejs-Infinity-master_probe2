<template> 
  <div id="app"> 
    <div id="login2" >
      <h1 id="titulo"><strong>∞INFINITY∞</strong></h1>
      
      <router-link to="/"  >Home</router-link> |
      <router-link to="/login" >Login</router-link>  |
      <router-link to="/signUp" >SignUp</router-link> |
      <router-link to="/index">Index</router-link> |
      <router-link to="/viewImage">Index</router-link> |
    </div>
    <router-view/>   
  </div>

</template>

<style>
#login2 {
 margin-top: 0px;
 background:#dede1f; 

} 

#titulo{
    font-size: 400%;
    color:#0419cc;
    font-family:courier; 

}

 
#app {
 
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;   
  
        background:#8ba987 url( http://i0.wp.com/wallpaperstock.net/digital-infinity-wallpapers_7472_1280x960.jpg)  no-repeat;
        background-size: cover;
        background-position: center right; width: 100%; height: 100vh; 
     
}
</style>
