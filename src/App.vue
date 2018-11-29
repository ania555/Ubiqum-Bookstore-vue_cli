<template>
  <div id="app">
    <div v-if="isLoading">
      <p>loading</p>
    </div>
    <div v-else>
      <!-- <Home :allBooks="myBooks"/> -->
      <div id="nav">
        <router-link :to="{ name: 'home', params: { booksForHome: this.myBooks }}">HOME</router-link> 
        <router-link :to="{ name: 'BooksList', params: { booksForList: this.myBooks }}">BOOKS LIST</router-link>
      </div>
      <router-view/>
    </div>

  </div>
</template>



<script>
import Home from '@/views/Home.vue'

export default {
  name: "App",
  components: {
    Home,
  },
  data() {
    return {
      myBooks: [],
      isLoading: true,
      num: 25,
    }
  },
  created() {
      let url = "https://api.myjson.com/bins/udbm5";
      fetch(url).then((response) => {
        return response.json()
    })
    .then((json) => {
        this.myBooks = json.books;
        this.isLoading = false;
        console.log(this.myBooks);        
    })
    .catch((error) => {
        console.log("Request failed: " + error.message)
    })
    },
    methods: {
    } 
}


</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: rgb(55, 118, 120);
} 

#nav a {
  color: rgb(115, 178, 180);;
  background-color: rgb(55, 118, 120);
  padding: 8px;
  margin-left: 50px;
  font-size: 20px;
  font-weight: 500;
}
#nav a:hover {
  text-decoration: none;
  color: orange;

}
#nav a.router-link-exact-active {
  color: white;
}

@import'~bootstrap/dist/css/bootstrap.css'
</style>
