<template>
  <div id="app">
    <div class="hero is-white is-gradient is-bold">
      <div class="hero-body">
        <h1 class="title">
          <span class="has-text-success">torre</span>
          <!-- <span class="subtitle">sub</span> -->
        </h1>

        <!-- <h1 class="title">Consultar datos</h1> -->
        <button class="button is-success is-rounded" v-on:click="fetch">
          Consulta
        </button>

        <div class="field has-addons is-pulled-right">
          <!-- <div class="control">
            <input
              v-model="search"
              type="text"
              class="input is-rounded"
              v-on:keyup.enter="searchData"
            />
          </div>

          <div class="control">
            <button
              class="button is-success is-rounded"
              v-on:click="searchData"
            >
              Buscar
            </button>
          </div> -->
        </div>
      </div>
    </div>

    <div class="column is-12-mobile is-4-desktop is-4-tablet">
      <div class="card">
        <div class="card-header p-4 flex-direction is-justify-content-center">
          <img
            v-bind:src="userName.pictureThumbnail"
            v-bind:alt="userName.name"
          />
        </div>

        <div class="card-container p-4">
          <span class="title is-size-6"
            >Name: <span class="is-size-6 has-text-weight-normal">{{ userName.name }}</span></span
          >
          <br />
          <span class="title is-size-6"
            >Profession:
            <span class="is-size-6 has-text-weight-normal">{{
              userName.professionalHeadline
            }}</span></span
          >
          <!-- <button class="button is-success is-rounded is-small" @click="showMore(character.id)">Ver mas</button> -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: "App",
  data: function() {
    return {
      userName: [],
    };
  },
  methods: {
    fetch() {
      // const params = {
      //   page: this.page,
      // };

      let result = axios
        .get(
          "https://thingproxy.freeboard.io/fetch/https://bio.torre.co/api/bios/choisjuliana"
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
      this.page = 1;
      this.fetch();
    },
  },
  // components: {
  //   HelloWorld
  // }
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
