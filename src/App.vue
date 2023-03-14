<template>
  <div id="app">
    <to-do />
  </div>
</template>

<script>
import ToDo from './components/ToDo.vue'

export default {
  name: 'App',
  components: {
    ToDo
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&display=swap');
/* font-family: 'DM Sans', sans-serif; */


* {
  box-sizing: border-box;
}

:root {
  /* --checkbox-color: rgb(202, 60, 60);
     */
  --checkbox-color: rgb(115, 240, 93);
  --checkbox-shadow: rgba(238, 156, 167, 0.2);
  --add-button: rgba(255, 255, 255, 0.7);
  --add-button-shadow: rgba(238, 156, 167, 0.4);
}

body {
  width: 100%;
  height: 100vh;
  margin: 0;
  padding: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  /* background-image: linear-gradient(109.6deg, rgba(156, 252, 248, 1) 11.2%, rgba(110, 123, 251, 1) 91.1%); SECOND OPTION*/
  background-image: linear-gradient(95.2deg, rgba(173, 252, 234, 1) 26.8%, rgba(192, 229, 246, 1) 64%);
  background-blend-mode: normal, lighten, multiply, hard-light;
  font-family: 'DM Sans', sans-serif;
  overflow: hidden;
}
</style>
