<template>
  <div class="user-card">
    <img
      class="image"
      :src="user.picture.large"
      :alt="`${user.name.first} ${user.name.last}`"
    />
    <h1 class="name">{{ user.name.first }} {{ user.name.last }}</h1>
    <h3 class="email">Email: {{ user.email }}</h3>
    <button @click="contactUser" class="btn">Contact</button>
  </div>
</template>

<script>
export default {
  name: "UserCard",
  props: {
    user: Object
  },
  methods: {
    contactUser() {
      window.open(`mailto:${this.user.email}`);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.user-card {
  background: white;
  width: 100%;
  max-width: 400px;
  height: 400px;
  margin: auto;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  box-shadow: rgb(0 0 0 / 15%) 1.95px 1.95px 2.6px;
}

.name,
.email {
  margin-bottom: 1rem;
  font-weight: normal;
}

.image {
  border-radius: 50%;
  border: 5px #333 solid;
  margin-bottom: 1rem;
}

.btn {
  cursor: pointer;
  display: inline-block;
  background: #333;
  color: white;
  font-size: 18px;
  border: 0;
  padding: 1rem 1.5rem;
}

.btn:focus {
  outline: none;
}

.btn:hover {
  transform: scale(0.98);
}

.male {
  border-color: steelblue;
  background-color: steelblue;
}

.female {
  border-color: pink;
  background-color: pink;
  color: #333;
}
</style>
