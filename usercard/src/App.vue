<template>
  <div id="app">
    <card v-for="user in users" :key="user.email" :user ="user"></card>
  </div>
</template>

<script>
import card from './components/Card.vue'
import axios from 'axios'
export default {
  name: 'app',
  data(){
    return {
      users: [],
    }
  },
  components: {
    card
  },
  mounted(){
    axios.get('https://randomuser.me/api/').then((response) => {
      this.users = response.data.results;
      console.log(response);
    })
  },

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
