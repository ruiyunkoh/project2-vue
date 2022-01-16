<template>
  <div>
   <div class="container-fluid">
     <nav class="nav sticky-top">
      <div id="exerciseLogo">
        <img alt="" src="./assets/logo.png">
      </div>
      <a class="nav-link active mx-2" aria-current="page" >HOME</a>
      <a class="nav-link mx-2">CREATE</a>  
     </nav>
   </div>
 </div>

</template>

<script>
export default {
  name: 'App',
  
};
</script>

<style>
#exerciseLogo > img{
  height: 80px;
  width: 60px;
}
</style>
