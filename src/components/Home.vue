<template>
  <div class="wrapper">
    <div class="col-1">
      <input v-on:change="ok" v-model="number" type="number" />
    </div>
    <div class="col-2">
      <select v-on:change="ok" name="work" v-model="work">
        <option value="isPrime">isPrime</option>
        <option value="isFibo">isFibo</option>
      </select>
    </div>
    <div class="col-3">
      {{ ans }}
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      number: "",
      ans: false,
      work: "isPrime",
    };
  },
  methods: {
    ok() {
      if (this.number !== "") {
        if (this.number < 0) {
          this.number = 1;
        }
        this.number = parseInt(this.number);
        if (this.work === "isPrime") {
          this.ans = this.isPrime(this.number);
        } else {
          this.ans = this.isFibonacci(this.number);
        }
      }
    },
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
    isFibonacci(n, current = 1, prev = 0) {
      const sum = current + prev;
      if (current == n || prev == n) {
        return true;
      } else if (current > n) {
        return false;
      } else {
        prev = current;
        return this.isFibonacci(n, sum, prev);
      }
    },
  },
};
</script>
<style scoped>
.wrapper {
  display: flex;
  height: 100vh;
  align-items: stretch;
}
.col-1 {
  width: 200px;
  border: 1px solid;
}
.col-2 {
  flex-grow: 1;
  border: 1px solid;
}
.col-3 {
  width: 300px;
  border: 1px solid;
}
</style>
