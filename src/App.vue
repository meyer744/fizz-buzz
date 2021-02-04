<template>
  <div>
    <h1>Fizz Buzz Vue</h1>
    <range-selection
      @fromValue="setFromValue"
      @toValue="setToValue"
      @runFizzBuzz="runFizzBuzz"
      :fizzBuzzButton="fizzBuzzButton"
    ></range-selection>
    <!-- <button @click="runFizzBuzz">{{ fizzBuzzButton }}</button> -->
    <fizz-buzz :fizzBuzz="fizzBuzz"></fizz-buzz>
  </div>
</template>

<script>
import RangeSelection from "./components/RangeSelection.vue";
import FizzBuzz from "./components/FizzBuzz.vue";
export default {
  name: "App",
  components: {
    RangeSelection,
    FizzBuzz,
  },
  methods: {
    setFromValue(v) {
      this.fromValue = v;
      console.log(this.fromValue);
    },
    setToValue(v) {
      this.toValue = v;
      console.log(this.toValue);
    },
    runFizzBuzz() {
      if (this.fizzBuzz.length < 1) {
        for (let i = this.fromValue; i <= this.toValue; i++) {
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
        console.log(this.fizzBuzz);
        console.log(this.to);
        console.log(this.from);
      } else {
        this.fizzBuzz = [];
      }
    },
  },
  computed: {
    fizzBuzzButton() {
      if (this.fizzBuzz.length < 1) {
        return "Run Fizz Buzz";
      } else {
        return "Clear";
      }
    },
  },
  data() {
    return {
      fizzBuzz: [],
      fromValue: null,
      toValue: null,
    };
  },
};
</script>

<style scoped>
@import "https://fonts.googleapis.com/css2?family=Russo+One&display=swap";

div {
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  font-size: 60px;
  font-family: "Russo One", sans-serif;
  color: #41B783;
  text-align: center;
}
</style>
