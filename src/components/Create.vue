<template>
  <div class="create-holder row">
    <h1>Share your routine!</h1>    
    <form class="row g-3 mt-3">
      <div class="col-md-8">
        <label class="form-label">Title:</label>
        <input type="text" class="form-control" v-model="title">
      </div>
      <div class="col-md-4">
        <label class="form-label">Your Name:</label>
        <input type="text" class="form-control" v-model="poster">
      </div>
      <div class="col-12">
        <label class="form-label">Exercise Image URL:</label>
        <input type="text" class="form-control" v-model="image">
      </div>
      <div class="col-12">
        <label class="form-label">Description:</label>
        <input type="text" class="form-control" v-model="description" placeholder="Enter short description of your routine">
      </div>
      <div class="mb-3">
        <label class="form-label">Exercise Moves:</label>
        <textarea class="form-control" v-model="routine" rows="3" placeholder="Separate each move by an exclamation mark"></textarea>
      </div>      
      <div class="col-md-4">
        <label class="form-label">Exercise Type:</label>
        <select v-model="type" class="form-select">
          <option selected value="HIIT">HIIT</option>
          <option value="Cardio">Cardio</option>
          <option value="Stretching">Stretching</option>
          <option value="Yoga/Pilates">Yoga/Pilates</option>
        </select>
      </div>
      <div class="col-md-4">
        <label class="form-label">Target Area:</label>
        <select v-model="targetArea" class="form-select">
          <option selected value="Whole body">Whole Body</option>
          <option value="Upper body">Upper body</option>
          <option value="Legs">Legs</option>
          <option value="Butt">Butt</option>
          <option value="Abs">Abs</option>
        </select>
      </div>
      <div class="col-md-2">
        <label class="form-label">Duration (mins):</label>
        <input type="text" class="form-control" v-model="duration">
      </div>
      <div class="col-md-2">
        <label class="form-label">Calories burnt:</label>
        <input type="text" class="form-control" v-model="caloriesBurnt">
      </div>
      <div class="me-2">
        <label class="ms-1 me-2">Intensity:</label>
        <input type="radio" name ="intensity" value="Beginner" v-model="intensity"> Beginner
        <input type="radio" name ="intensity" value="Intermediate" v-model="intensity"> Intermediate
        <input type="radio" name ="intensity" value="Advanced" v-model="intensity"> Advanced
      </div>
      <div>
        <label class="ms-1 me-2">Tags:</label>
        <div>
        <input class="ms-2" type="checkbox" value="No equipment required" v-model="tags"> No equipment required
        <input class="ms-2" type="checkbox" value="No jumping" v-model="tags"> No jumping
        </div>
      </div>
      <p class="text-danger" v-if="errors.length"><b>! Please ensure all fields are filled</b></p>
      <button v-on:click="addNew" type="button" class="create-btn btn-outline-secondary col-1 my-3">Add</button>
      
    </form>
  </div>
</template>

<script>
import axios from "axios";

const API_URL = "https://kry-exercise.herokuapp.com";

export default {
  name: 'Create',
  data: function () {
    return {
      poster: "",
      title: "",
      image: "",
      duration: "",
      description: "",
      routine: "",
      type: "",
      intensity: "",
      targetArea: "",
      caloriesBurnt: "",
      tags: [],
      errors: []
    };
  },
  methods: {
   addNew: async function () {
     this.errors = [];
     if (!this.poster || !this.title || !this.duration || !this.description || !this.routine || !this.type || !this.intensity || !this.targetArea || !this.caloriesBurnt) {
       this.errors.push("Field required");
     }
     else {
     let response = await axios.post(API_URL + "/new_exercise", {
      poster: this.poster,
      title: this.title,
      image: this.image,
      duration: parseInt(this.duration),
      description: this.description,
      routine: this.routine.split('!'),
      type: this.type,
      intensity: this.intensity,
      targetArea: this.targetArea,
      caloriesBurnt: parseInt(this.caloriesBurnt),
      tags: this.tags
     });
     console.log(response.data);
     this.$emit("new-exercise-created")}
    },
 },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Shippori+Antique&display=swap");
.create-holder>h1{
  display: flex;
  justify-content: center;
  font-family: "Roboto Condensed", sans-serif;
  margin-top: 10px;
}
.create-holder{
  display: flex;
  justify-content: center;  
}
form {
  max-width: 800px !important;
  
}

</style>