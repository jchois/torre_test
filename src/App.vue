<template>
  <div id="app">
    <div class="hero is-white is-gradient is-bold">
      <div class="hero-body">
        <h1 class="title">
          <span class="has-text-success">torre</span>
          <!-- <span class="subtitle">sub</span> -->
        </h1>

        <div class="field has-addons is-pulled-left">
          <div class="control">
            <input
              id="inputUsername"
              v-model="search"
              type="text"
              class="input is-rounded"
              v-on:keyup.enter="searchData"
              placeholder="username"
            />
          </div>

          <div class="control">
            <button
              class="button is-success is-rounded"
              v-on:click="searchData"
            >
              Search
            </button>
          </div>
        </div>
      </div>
    </div>

    <user v-bind:userName="userName" />
  </div>
</template>

<script>
import axios from "axios";

// import HelloWorld from './components/HelloWorld.vue'
import User from "./components/User.vue";

export default {
  name: "App",
  data: function() {
    return {
      userName: [],
      search: '',
    };
  },
  methods: {
    fetch() {
      // const params = {
      //   page: this.page,
      //   name: this.search,
      // };

      let result = axios
        .get(
          `https://thingproxy.freeboard.io/fetch/https://bio.torre.co/api/bios/${this.search}`
        )
        .then((res) => {
          this.userName = res.data.person;
          console.log(res.data);
          console.log(res.data.person.name);
        })
        .catch((err) => {
          console.log(err);
        });
      console.log("edadfas");
    },
    searchData() {
      // this.page = 1;
      this.fetch();
    },
  },
  components: {
    User,
  },
};
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
