<template>
 <div class="create-holder row">
    <h1>Edit your routine!</h1>
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
        <input type="text" class="form-control" v-model="description">
      </div>
      <div class="mb-3">
        <label class="form-label">Routine:</label>
        <textarea class="form-control" v-model="routine" rows="3"></textarea>
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
        <select v-model="target_area" class="form-select">
          <option selected value="Whole Body">Whole Body</option>
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
        <input type="text" class="form-control" v-model="calories_burnt">
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
      <button v-on:click="processUpdate" type="button" class="create-btn btn-outline-secondary col-1 my-3">Update</button>
      
    </form>
  </div>
</template>

<script>
import axios from "axios";

const API_URL = "https://kry-exercise.herokuapp.com";

export default {
 name: "EditExercise",
 props: ["exerciseId"],
 data: function() {
     return {
        poster: "",
      title: "",
      image: "",
      duration: "",
      description: "",
      routine: "",
      type: "",
      intensity: "",
      "target_area": "",
      "calories_burnt": "",
      tags: [] 
     };
 },
 mounted: async function (){
     let response = await axios.get(API_URL + "/find_exercise/" + this.exerciseId);
     this.poster = response.data.poster;
     this.title = response.data.title;
     this.image = response.data.image;
     this.duration = response.data.duration;
     this.routine = response.data.routine;
     this.type = response.data.type;
     this.intensity = response.data.intensity;
     this.target_area = response.data.target_area;
     this.calories_burnt = response.data.calories_burnt;
     this.tags = response.data.tags;
 },
 methods: {
   processUpdate: async function () {
     let response = await axios.put(API_URL + "/find_exercise/" + this.exerciseId, {
       poster: this.poster,
      title: this.title,
      image: this.image,
      duration: this.duration,
      description: this.description,
      routine: this.routine.split('!'),
      type: this.type,
      intensity: this.intensity,
      target_area: this.target_area,
      calories_burnt: this.calories_burnt,
      tags: this.tags
     });
     console.log(response.data);
     this.$emit("exercise-updated");
   },
 },
};
</script>

<style>

</style>
