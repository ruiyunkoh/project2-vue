<template>
<div class="exercise-holder row">
  <form class="row g-3">      
      <div class="col-md-4">
        <label> Select type: </label>        
        <select class="form-select" v-model="type">
          <option value="">Select type</option>          
          <option value="HIIT">HIIT</option>
          <option value="Cardio">Cardio</option>
          <option value="Stretching">Stretching</option>
          <option value="Yoga/Pilates">Yoga/Pilates</option>
        </select>
      </div>
      <div class="col-md-4">
        <label>Select Intensity: </label>
        <select class="form-select" v-model="intensity">
          <option value="">Select intensity</option>          
          <option value="Beginner">Beginner</option>
          <option value="Intermediate">Intermediate</option>
          <option value="Advanced">Advanced</option>
        </select>
      </div>
      <div class="col-md-4">
        <label> Select Target Area: </label>        
        <select class="form-select" v-model="targetArea">
          <option value="">Select target area</option>          
          <option value="Whole body">Whole Body</option>
          <option value="Upper body">Upper Body</option>
          <option value="Legs">Legs</option>
          <option value="Abs">Abs</option>
        </select>
      </div>
    </form>
  <p> Total of {{totalResults}} results displayed </p> 
  <div class="card m-3" v-for="x in filteredExercises" v-bind:key="x._id">
    <img v-bind:src="x.image" class="card-img-top" alt="">
    <div class="card-body">
      <a class="card-title text-black" v-on:click="selected(x._id)">{{x.title}}</a>
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

const API_URL = "https://kry-exercise.herokuapp.com";

export default {
  name: 'Exercises',
  
  data: function() {
    return{
      exerciseList: [],      
      targetArea: '',
      type:'',
      intensity: '',
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
    selected: function (exerciseId) {
      this.$emit("selected-exercise", exerciseId);
    },
    deleteExercise: function(exerciseId){      
      this.$emit("delete-exercise", exerciseId);      
    },
    
  },
  computed: {
    filteredExercises: function() {
      let filtered = this.exerciseList.filter((eachExercise)=>{
        return eachExercise.targetArea.includes(this.targetArea)
      });
      filtered = filtered.filter((eachExercise)=>{
        return eachExercise.type.includes(this.type)
      });
      filtered = filtered.filter((eachExercise)=>{
        return eachExercise.intensity.includes(this.intensity)
      });
      return filtered;
    },
    totalResults: function() {
      return this.filteredExercises.length
      }
    
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;800&family=Roboto+Condensed:wght@700&display=swap");
.exercise-holder{
  display: flex;
  justify-content: center;
}
.exercise-holder>p{
  margin-top: 10px;
  text-align: center;
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
