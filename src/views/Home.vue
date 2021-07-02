<template>
  <div class="home">

  <div class="p-5 d-flex flex-wrap justify-content-between"> 
    <div v-for="course in courses" v-bind:key = 'course' class="h-100">
      <b-card
        :title="course.course_name"
        tag="article"
        style="max-width: 20rem;"
        class="mb-2"
      >
        <b-img :src="course.image" class="card-img"></b-img>
        <b-card-text class="card-description">
          <p>{{course.description}}</p>
        </b-card-text>

        <b-button href="#list" @click="usersList(course.id)" variant="primary">Users Subscribed</b-button>


       

     


      </b-card>
    </div>
  </div>
    <div id="list" class="users">
          <ul>
            <li v-for="user in subscribers" v-bind:key = 'user'>
              <p>{{user.name}}</p>
              
            </li>
        </ul>
    </div>

   </div>

 
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import axios from 'axios';
import ShowUserList from '@/views/ShowUserList.vue';

export default {
  name: 'Home',

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

<style lang="scss">
  
  .card-img {
    width: 100%;
    height: 15vw;
    object-fit: cove
  }

  .card-description {
    text-overflow: ellipsis !important;
    max-height: 30% !important;
  } 
</style>