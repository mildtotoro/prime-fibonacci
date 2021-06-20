<template>
  <div class="wrapper">
    <div class="col-1">
      <input v-model="number" type="number" />
    </div>
    <div class="col-2">b</div>
    <div class="col-3">c</div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      number: "",
    };
  },
  watch: {
    number(value) {
      if (value) {
        value = 1;
        console.log({ value });
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
html,
body {
  overflow: hidden;
  padding: 0px;
  margin: 0px;
}
@media screen and (max-width: 600px) {
  body {
    overflow: scroll;
  }
}

.wrapper {
  display: flex;
  height: 100vh;
  align-items: stretch;
}
.col-1 {
  background-color: aquamarine;
  width: 200px;
}
.col-2 {
  background-color: bisque;
  flex-grow: 1;
}
.col-3 {
  background-color: coral;
  width: 300px;
}
</style>
