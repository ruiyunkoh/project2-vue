<template>
  <div>
   <div class="container-fluid">
    <div class="alert alert-success" v-if="status">{{ status }}</div>
     <nav class="nav sticky-top">
      <div id="exerciseLogo">
        <img alt="" src="./assets/logo.png">
      </div>
      <a class="nav-link active mx-2 text-black" aria-current="page" v-on:click="goHome" >HOME</a>
      <a class="nav-link mx-2 text-black" aria-current="page" v-on:click="goExercises" >EXERCISES</a>
      <a class="nav-link mx-2 text-black" v-on:click="goCreate" >CREATE</a>  
     </nav>
     <div>
       <Home v-if="page == 'home'" @gotoExercises="goExercises" /> 
       <Exercises v-if="page == 'exercises'" v-on:update-exercise="updateExercise" v-on:delete-exercise="confirmDelete" v-on:selected-exercise="exerciseSelected" />
       <Create v-if="page == 'create'" v-on:new-exercise-created="newExerciseCreated"/>
       <EditExercise v-if="page == 'edit'" v-bind:exerciseId="exerciseBeingEdited" v-on:exercise-updated="exerciseUpdated"/>
       <SelectedExercise v-if="page == 'select'" v-bind:exerciseId="exerciseIsSelected" />
       <DeleteExercise v-if="page == 'delete'" v-bind:exerciseId="exerciseBeingDeleted" v-on:exercise-deleted="exerciseDeleted" v-on:cancel-exercise="goExercises"/>
     </div>

   </div>
 </div>

</template>

<script>
import Home from "./components/Home";
import Exercises from "./components/Exercises";
import Create from "./components/Create";
import EditExercise from "./components/EditExercise";
import SelectedExercise from "./components/SelectedExercise";
import DeleteExercise from "./components/DeleteExercise";

export default {
  name: 'App',
  components:{
    Home, Exercises, Create, EditExercise, SelectedExercise, DeleteExercise
  },
  data:function(){
   return {
     'page':'home'
   }
 },
 methods: {
   goHome: function() {
     this.page = "home";
     this.status = "";
   },
   goExercises: function () {
     this.page = "exercises";
     this.status = "";
   },
   goCreate: function () {
     this.page = "create";
     this.status = "";
   },
   newExerciseCreated: function() {
     this.page ="exercises";
     this.status = "New Exercise Routine added";
   },
   updateExercise: function (exerciseId) {
     this.page = "edit";
     this.status = "";
     this.exerciseBeingEdited = exerciseId;
   },
   exerciseUpdated: function (){
     this.page = "exercises";
     this.status = "Exercise Routine updated";
   },
   confirmDelete: function(exerciseId) {
     this.page = "delete";
     this.status = "";
     this.exerciseBeingDeleted = exerciseId;
   }, 
   exerciseDeleted: function (){    
     this.page = "exercises";
     this.status = "Exercise routine deleted";
   },
   exerciseSelected: function(exerciseId) {
     this.page = "select";
     this.exerciseIsSelected = exerciseId;
     this.status = "";
   }
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
