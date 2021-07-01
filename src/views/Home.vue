<template>
  <div class="home">
      <!-- <h1 @click="changetext">Hola Sergio</h1> -->
      <!-- <div>
        <ul>
            <li v-for="course in courses" :key = 'course'>
              <p>{{course.course_name}}</p>
              <router-link to="/ShowUserList">User List</router-link> 
              <button @click="usersList(course.id)">Users subscribed</button>
            </li>
        </ul>
      </div> -->
  <div v-for="course in courses" v-bind:key = 'course'>
  <b-card
    :title="course.course_name"
    :img-src="course.image"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-2"
  >
    <b-card-text>
      {{course.description}}
    </b-card-text>

    <b-button @click="usersList(course.id)" variant="primary">Users Subscribed</b-button>
  </b-card>
</div>
 <div class="users">
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