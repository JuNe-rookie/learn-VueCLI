<template>
  <div id="app">
    <h1>{{msg}}</h1>
    <School/>
    <Student/>
  </div>
</template>

<script>
import School from "./components/School.vue";
import Student from "./components/Student.vue"

export default {
  name: "App",
  components: {
    School,
    Student
  },
  data(){
    return {
      msg:'hello'
    }
  },
};
</script>

<style>
  #app{
    background-color: #cccccc;
  }
</style>