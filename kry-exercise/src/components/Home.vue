<template>
  <div>
    <div class="banner">
        <img alt="" src="../assets/banner.png">
        <div class="text">
        <h1 v-bind:style="styleObject">Share & Shed</h1>
        <p>A place to uncover exercise routines shared</p>
        <p>by a community that prioritises wellness.</p>
        </div>
        <button type="button" class="btn btn-outline-light" v-on:click="findExercise">Find Exercises</button>
    </div>
    </div>
</template>

<script>
export default {
  name: 'Home',
  data: function(){
      return{
      styleObject:{
          fontSize:"60px"
      }
      }
  },
  methods: {
      findExercise: function(){
          this.$emit("gotoExercises")
      }
  }   
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;800&family=Roboto+Condensed:wght@700&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Shippori+Antique&display=swap");
.banner {
    position: relative;
    text-align: center;
    color: white;
}
.banner>img{
    height: calc(100vh - 80px);
    width: 100%;
}
.text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
.btn{
    position: absolute;
    bottom: 30%;
    left: 50%;
    transform: translate(-50%, -50%);
}
.text>h1{
    font-family: "Roboto Condensed", sans-serif;
}
.text>p{
    line-height: 0.5;
    font-family: "Montserrat", sans-serif;
}


</style>