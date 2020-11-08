<template>
  <div id="app">
    <div class="hero is-white is-gradient is-bold">
      <div class="hero-body">
        <div class="mb-6 title-content">
          <img id="torreLogo" alt="torre_logo" src="./assets/torre.png" />
          <h1 class="title ml-1">
            <span class="">torre</span>
          </h1>
        </div>

        <div class="field has-addons is-pulled-left">
          <div class="control">
            <input
              id="inputUsername"
              v-model="search"
              type="text"
              class="input is-rounded"
              v-on:keyup.enter="searchData"
              placeholder="Type your username"
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

import User from "./components/User.vue";

export default {
  name: "App",
  data: function() {
    return {
      userName: [],
      search: "",
    };
  },
  methods: {
    fetch() {

      let result = axios
        .get(
          `https://thingproxy.freeboard.io/fetch/https://bio.torre.co/api/bios/${this.search}`
        )
        .then((res) => {
          this.userName = res.data.person;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    searchData() {
      this.fetch();
    },
  },
  components: {
    User,
  },
};
</script>

<style>
.hero{
  box-shadow: 0 0.125em 0.25em rgba(10, 10, 10, 0.3);
}
#torreLogo {
  width: 30%;
}
.hero-body{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.title-content{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
