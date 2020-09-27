<template>
  <div id="app">
    <NavBar v-on:search="search"/>
    <b-container>
      <b-row>
        <PictureBox v-for="pic in pictures" :key="pic.id" :pic="pic"/>  <!-- :picでデータをpicturebox渡す -->
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from "axios";
import NavBar from "./components/NavBar.vue";
import PictureBox from "./components/PictureBox";
const URL_BASE ="https://pixabay.com/api/";
const API_KEY ="18398808-9350dfa5897a30784ac37767b";

export default {
  name: 'App',
  components: {
    NavBar,
    PictureBox
  },
  data(){
    return{pictures: []};
  },
  methods:{
    search(word){
      let self = this;
        global.console.log("App.vue:" + word); // this = VueConpornent
      axios
      .get(URL_BASE, {
        params:{
          q: encodeURIComponent(word),
          key: API_KEY
        }
      })
      .then(function(response){
        self.pictures = response.data.hits;
      });
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
