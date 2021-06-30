<template>
  <div class="home">
       <h1 @click="changetext">{{text}}</h1>
       <div v-for="event in list">
         {{event.nombre}}
       </div>
       <HelloWorld msg="Welcome to Your Vue.js App"/>
       
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import Axios from '@/components/Axios.vue';

export default {
  name: 'Home',
  components: {
    Axios
  },
  data(){
    return {
      text:"Hola World2",
      courses:[]
    }
  },
  methods:{
    changetext(){
      this.text="Vamos a la playa"
    }
  },

  created() {
    Axios.get(url).then(response => console.log(response))

  }
}
 </script>

