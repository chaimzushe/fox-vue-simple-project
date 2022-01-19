<template>
  <header class="header">
    <button @click="$emit('generate-users')" class="btn">Load random users</button>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.header {
  margin: 0;
  text-align: end;
  padding: 22px;
  border: 1px solid;
  background: black;
  display: flex;
  justify-content: flex-end;
  align-items: flex-end;
}

.btn {
  border-radius: 3px;
  display: inline-block;
  cursor: pointer;
  font-family: Arial;
  font-size: 13px;
  padding: 12px 24px;
  text-shadow: 0px 1px 0px #154682;
  background: white;
  color: black;
  border: none;
}

</style>
