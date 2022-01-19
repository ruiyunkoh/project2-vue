<template>
<div class="exercise-holder row">
  <div class="card m-3" v-for="x in exerciseList" v-bind:key="x._id">
    <img v-bind:src="x.image" class="card-img-top" alt="">
    <div class="card-body">
      <a class="card-title text-black">{{x.title}}</a>
      <p class="card-text">{{x.description}}</p>
      <span class="badge bg-secondary me-2">{{x.tags[0]}}</span>
      <span class="badge bg-dark">{{x.tags[1]}}</span>
      <p class="card-text"><small class="text-muted">Shared by: {{x.poster}} </small></p>
    </div>
  </div>
</div>
</template>

<script>
import axios from "axios";

const API_URL = "https://kry-exercise.herokuapp.com";

export default {
  name: 'Exercises',
  data: function() {
    return{
      exerciseList: [],
    };
  },
  mounted: async function () {
    let response = await axios.get(API_URL + "/find_exercise");
    this.exerciseList = response.data;
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
</style>
