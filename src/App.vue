<template>
  <div>
    <button @click="runFizzBuzz">{{ fizzBuzzButton }}</button>
    <ul>
      <li :class="n === 'fizz buzz' ? 'fizzbuzz' : n" v-for="(n, i) in fizzBuzz" :key="i">{{ n }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  computed: {
    fizzBuzzButton() {
      if(this.fizzBuzz.length < 1) {
        return 'Run Fizz Buzz';
      } else {
        return 'Clear'
      }
    }
  },
  data() {
    return {
      fizzBuzz: [],
    };
  },
  methods: {
    runFizzBuzz() {
      if (this.fizzBuzz.length < 1) {
        for (let i = 1; i <= 100; i++) {
          if (i % 3 === 0 && i % 5 === 0) {
            this.fizzBuzz.push("fizz buzz");
          } else if (i % 3 === 0 && i % 5 != 0) {
            this.fizzBuzz.push("fizz");
          } else if (i % 5 === 0 && i % 3 != 0) {
            this.fizzBuzz.push("buzz");
          } else {
            this.fizzBuzz.push(i.toString());
          }
        }
      } else {
        this.fizzBuzz = [];
      }
    },
  },
};
</script>

<style>
@import"https://fonts.googleapis.com/css2?family=Russo+One&display=swap";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  max-width: 400px;
  margin: auto;
}


ul {
  list-style: none;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;
}

li {
  padding: 15px;
  margin: 5px;
  border-style: solid;
  border-radius: 6px;
}

.fizz {
  color: red;
}

.buzz {
  color: green;
}

.fizzbuzz {
  color: blue;
}

button {
  margin-top: 20px;
  font-family: 'Russo One', sans-serif;
  background-color: transparent;
  border-style: solid;
  border-radius: 5px;
  border-width: 4px;
  border-color: black;
  padding: 10px;
  font-size: 30px
}
</style>
