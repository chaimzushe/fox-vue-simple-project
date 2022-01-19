<template>
  <Header @generate-users="generateUsers()" />

  <h3  class="header">Meet our Crew</h3>
  <div v-show="loading" class="loader">
    <Loader />
  </div>
  <div class="list">
    <UserCard :key="user.id" v-for="user in users" :user="user" />
  </div>
</template>

<script>
import UserCard from "./components/UserCard.vue";
import Header from "./components/Header.vue";
import Loader from "./components/Loader.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    UserCard,
    Header,
    Loader,
  },
  data() {
    return {
      users: [],
      loading: true,
    };
  },
  methods: {
    generateUsers() {
      this.loading = true;
      this.user = [];
      axios.get("https://randomuser.me/api?results=20").then((response) => {
        this.loading = false;
        this.users = response.data.results;
      });
    },
  },
  mounted() {
    this.generateUsers();
  },
};
</script>

<style>
body {
  background-color: #f5f4f4;
  font-family: sans-serif;
  margin: 0;
}
.loader {
  position: absolute;
  left: 50%;
  transform: translate(-50%, 0);
}
.header {
  font-size: 52px;
  margin: 52px auto;
  text-align: center;
  font-weight: bold;
}
.list {
  display: grid;
  grid-gap: 30px;
  grid-template-columns: repeat(auto-fit, minmax(500px, 1fr));
  box-sizing: border-box;
}
@media(max-width: 500px) {
  .list {
    grid-template-columns: 1fr
  }
  .header {
      font-size: 40px;
  }
}
</style>
