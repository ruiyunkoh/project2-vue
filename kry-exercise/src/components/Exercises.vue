<template>
<div class="exercise-holder row">
  <div>
    <SearchExercise v-if="page == 'exercises'" />
  </div>
  <div class="card m-3" v-for="x in exerciseList" v-bind:key="x._id">
    <img v-bind:src="x.image" class="card-img-top" alt="">
    <div class="card-body">
      <a class="card-title text-black">{{x.title}}</a>
      <p class="card-text">{{x.description}}</p>
      <span class="badge bg-secondary me-2">{{x.tags[0]}}</span>
      <span class="badge bg-dark">{{x.tags[1]}}</span>
      <div class="icons">
        <font-awesome-icon class="edit-btn me-2" icon="edit" v-on:click="update(x._id)" />
        <font-awesome-icon class="delete-btn" icon="trash" v-on:click="deleteExercise(x._id)"/>
      </div>
      <p class="card-text"><small class="text-muted">Shared by: {{x.poster}} </small></p>
    </div>
  </div>
</div>
</template>

<script>
import axios from "axios";
import SearchExercise from "./SearchExercise";

const API_URL = "https://kry-exercise.herokuapp.com";

export default {
  name: 'Exercises',
  components:{
    SearchExercise
  },
  data: function() {
    return{
      exerciseList: [],
      'page':'exercises'
    };
  },
  mounted: async function () {
    let response = await axios.get(API_URL + "/find_exercise");
    this.exerciseList = response.data;
  },
  methods: {
    update: function (exerciseId) {
      this.$emit("update-exercise", exerciseId);
    },
    deleteExercise: async function(Id){
      let response = await axios.delete(API_URL + "/find_exercise/" + Id); 
      this.$emit("delete-exercise");
      console.log(response.data);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;800&family=Roboto+Condensed:wght@700&display=swap");
.exercise-holder{
  display: flex;
  justify-content: center;
}
.card {
  max-width: 800px !important;
}
.card-img-top{
  max-width: 800px;
  height: 350px;
}
.card-title{
  font-family: "Roboto Condensed", sans-serif;
  font-size: 25px;
  text-decoration: none;
}
.card-title:hover{
  color: rgb(142,142,142)!important;
}
.icons{
  display:flex;
  justify-content: flex-end;
}
</style>
