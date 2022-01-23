<template>
  <div class="search-holder mt-3">
    <form class="row g-3">
      <div class="col-md-4">
          <label> Search </label>
        <input type="text" v-model="title" placeholder="Search by title" />
      </div>
      <div class="col-md-3">
        <label> Select type: </label>        
        <select class="form-select" v-model="type">          
          <option value="HIIT">HIIT</option>
          <option value="Cardio">Cardio</option>
          <option value="Stretching">Stretching</option>
          <option value="Yoga/Pilates">Yoga/Pilates</option>
        </select>
      </div>
      <div class="col-md-3">
        <label>Select Intensity: </label>
        <select class="form-select" v-model="intensity">          
          <option value="Beginner">Beginner</option>
          <option value="Intermediate">Intermediate</option>
          <option value="Advanced">Advanced</option>
        </select>
      </div>      
      <div class="col-2 pt-4">
        <button type="submit" class="searchbtn btn-sm btn-outline-secondary">Search</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchExercise",
};
</script>

<style>
.search-holder{
  display: flex;
  justify-content: center;
  
}
form {
  max-width: 800px !important;  
}
</style>
