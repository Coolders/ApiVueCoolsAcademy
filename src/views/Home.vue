<template>
  <div class="home">
      <h1 @click="changetext">{{text}}</h1>
      <div>
        <ul v-for="course in courses" :key = 'course'>
          <li>{{course.course_name}}</li>
        </ul>
      </div>
      <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import axios from 'axios';

export default {
  name: 'Home',

  data(){
    return {
      text:"Hola World2",
      courses:[]
    }
  },


  mounted() {
    axios.get('http://127.0.0.1:8000/api/courses').then(response => {
            this.courses = response.data;
    });


  }
}
</script>