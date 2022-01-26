<template>
<div class="selected-holder">
  <div class="card m-3">    
    <div class="card-body">
      <h1 class="cardselected-title text-black">{{exerciseItem.title}}</h1>
      <p class="card-text">{{exerciseItem.description}}</p>
      <span class="badge bg-secondary me-2">{{exerciseItem.tags[0]}}</span>
      <span class="badge bg-dark">{{exerciseItem.tags[1]}}</span>      
      <p class="card-text"><small class="text-muted">Shared by: {{exerciseItem.poster}} </small></p>
    </div>
    <img v-bind:src="exerciseItem.image" class="card-img-top" alt="">
    <div class="minicard-body m-3 col-md-6">
      <h5>Routine information</h5>
      <p class="card-text">Duration: {{exerciseItem.duration}} minutes</p>
      <p class="card-text">Type: {{exerciseItem.type}}</p>
      <p class="card-text">Intensity: {{exerciseItem.intensity}}</p>
      <p class="card-text">Target Area: {{exerciseItem.targetArea}}</p>
      <p class="card-text">Calories Burnt: {{exerciseItem.caloriesBurnt}}</p>
    </div>
    <div class="routinecard-body m-3">
      <h5>Routine Moves</h5>
      <p class="card-text" v-for="(item, index) in exerciseItem.routine" :key="index">{{item}}</p>
    </div>
  </div>
</div>
</template>

<script>
import axios from "axios";

const API_URL = "https://kry-exercise.herokuapp.com";

export default {
  name: 'SelectedExercise',
  props: ["exerciseId"],
  data: function(){
      return {
          exerciseItem: [],
      };
  },
  mounted: async function() {
      let response = await axios.get(API_URL + "/find_exercise/" + this.exerciseId);
      this.exerciseItem = response.data;
  },
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;800&family=Roboto+Condensed:wght@700&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Shippori+Antique&display=swap");

.selected-holder{
    display: flex;
    justify-content: center;
}
.cardselected-title{
  font-family: "Roboto Condensed", sans-serif;
  font-size: 30px;  
}
.minicard-body > p{
  margin: 0;
  font-family: "Montserrat", sans-serif;
  font-size: smaller;
}
.minicard-body > h5{
  font-family: "Roboto Condensed", sans-serif;
}
.routinecard-body > p{
  margin: 0;
  font-family: "Montserrat", sans-serif;
  font-size: smaller;
}
.routinecard-body > h5{
  font-family: "Roboto Condensed", sans-serif;
}
</style>