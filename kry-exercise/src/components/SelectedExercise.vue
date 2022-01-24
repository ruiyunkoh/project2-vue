<template>
<div class="selected-holder">
    <div class="card m-3">    
    <div class="card-body">
      <h2 class="cardselected-title text-black">{{exerciseItem.title}}</h2>
      <p class="card-text">{{exerciseItem.description}}</p>
      <span class="badge bg-secondary me-2">{{exerciseItem.tags[0]}}</span>
      <span class="badge bg-dark">{{exerciseItem.tags[1]}}</span>      
      <p class="card-text"><small class="text-muted">Shared by: {{exerciseItem.poster}} </small></p>
    </div>
    <img v-bind:src="exerciseItem.image" class="card-img-top" alt="">
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

.selected-holder{
    display: flex;
    justify-content: center;
}
.cardselected-title{
  font-family: "Roboto Condensed", sans-serif;
  font-size: 25px;
  
}
</style>