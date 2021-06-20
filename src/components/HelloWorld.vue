<template>
  <div class="wrapper">
    <div class="col-1">
      <input v-model="number" type="number" />
      <button @click="ok">ok</button>
    </div>
    <div class="col-2">
      {{ number }}
      // ans = {{ ans }}
    </div>
    <div class="col-3">
      c
      <pre>
      {{ temp }}
      </pre>
    </div>
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
      ans: false,
      temp: [],
    };
  },
  watch: {},
  mounted() {
    this.temp[1] = "true";
  },
  methods: {
    ok() {},
    isPrime(n, i = 2) {
      const max = n - 1;
      if (n === 2 || n === 1) {
        return true;
      }
      if (i === max) {
        return true;
      }
      if (n % i === 0) {
        return false;
      } else {
        i = i + 1;
        return this.isPrime(n, i);
      }
    },
    isFibo(n, current = 1, prev = 1) {
      const sum = current + prev;
      prev = current;
      if (current === n) {
        return true;
      } else if (current > n) {
        return false;
      } else {
        return this.isFibo(n, sum, prev);
      }
    },
  },
};
</script>
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
