<template>
  <div class="ShowUserList">
      <!-- <h1 @click="changetext">Hola Sergio</h1> -->
      <h1>hi</h1>
     
   </div>

 
</template>

<script>
// @ is an alias to /src

import axios from 'axios';

export default {
  name: 'ShowUserList',

  data(){
    return {
      text:"Hola World2",
      courses:[],
      subscribers:[]
    }
  },

  mounted() {
    axios.get('http://127.0.0.1:8000/api/courses').then(response => {
            this.courses = response.data;
    });

  },

  methods: {
    usersList(id) {
    axios.get(`http://127.0.0.1:8000/api/courses/${id}/subscribers`).then(response => {
            this.subscribers = response.data} ); console.log(this.subscribers)}
  }
  
            
}
</script>