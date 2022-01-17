<template>
  <div>
   <div class="container-fluid">
     <nav class="nav sticky-top">
      <div id="exerciseLogo">
        <img alt="" src="./assets/logo.png">
      </div>
      <a class="nav-link active mx-2 text-black" aria-current="page" v-on:click="goHome" >HOME</a>
      <a class="nav-link mx-2 text-black" aria-current="page" v-on:click="goExercises" >EXERCISES</a>
      <a class="nav-link mx-2 text-black" v-on:click="goCreate" >CREATE</a>  
     </nav>
     <div>
       <Home v-if="page == 'home'" /> 
       <Exercises v-if="page == 'exercises'" />
       <Create v-if="page == 'create'" />
     </div>

   </div>
 </div>

</template>

<script>
import Home from "./components/Home";
import Exercises from "./components/Exercises";
import Create from "./components/Create";
export default {
  name: 'App',
  components:{
    Home, Exercises, Create
  },
  data:function(){
   return {
     'page':'home'
   }
 },
 methods: {
   goHome: function() {
     this.page = "home";
   },
   goExercises: function () {
     this.page = "exercises";
   },
   goCreate: function () {
     this.page = "create";
   },
 },

};
</script>

<style>
#exerciseLogo > img{
  height: 80px;
  width: 60px;
  margin-left: 20px;
}

.nav {
  display: flex;
  align-items: center;
  background-color: rgb(215, 200, 200);
}

.nav-link:hover{
  color: rgb(255,255,255)!important;
}
</style>
