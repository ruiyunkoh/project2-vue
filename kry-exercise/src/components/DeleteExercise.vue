<template>
  <div class="delete-holder">
    <div class="deletecard">
      <div class="card-body">
        <h5 class="deletecard-title">Confirm Deletion of Routine</h5>
        <p class="card-text">
          Are you sure you wish to delete {{exerciseItem.title}} ?
        </p>
        <button v-on:click="deleteExercise" type="button" class="delete-btn btn-danger me-3">Delete</button>
        <button v-on:click="cancelExercise" type="button" class="cancel-btn btn-secondary my-3">Cancel</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

const API_URL = "https://kry-exercise.herokuapp.com";

export default {
  name: "DeleteExercise",
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
  methods: {
    deleteExercise: async function () {
    let response = await axios.delete(API_URL + "/find_exercise/" + this.exerciseId);
    this.$emit("exercise-deleted");
    console.log(response.data);
    },
    cancelExercise: function () {
        this.$emit("cancel-exercise");
    }
  },
};
</script>

<style>
.delete-holder{
    display: flex;
    justify-content: center;
}
.deletecard {
  max-width: 800px !important;
}
</style>