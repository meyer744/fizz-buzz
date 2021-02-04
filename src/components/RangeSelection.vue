<template>
  <h3>Set Range</h3>
  <form>
    <div class="row align-items-center">
      <div class="col">
        <input
          @input="$emit('fromValue', Number($event.target.value))"
          ref="fromInput"
          type="number"
          class="form-control"
          placeholder="From"
          @focus="invalid = false"
        />
      </div>
      <div class="col">
        <input
          @input="$emit('toValue', Number($event.target.value))"
          ref="toInput"
          type="number"
          class="form-control"
          placeholder="to"
          @focus="invalid = false"
        />
      </div>
    </div>
  </form>
  <p v-if="invalid">Please enter a valid range!</p>
  <button @click="sendFizzBuzz">{{ fizzBuzzButton }}</button>
</template>

<script>
export default {
  emits: ["fromValue", "toValue", "runFizzBuzz"],
  props: ["fizzBuzzButton"],
  methods: {
    sendFizzBuzz() {
      let from = this.$refs.fromInput.value;
      let to = this.$refs.toInput.value;
      if (from === "" || to === "" || Number(from) > Number(to)) {
        this.invalid = true;
      } else {
        this.$emit("runFizzBuzz");
        this.clickNumber++;
        console.log(this.clickNumber);
        if (this.clickNumber % 2 === 0) {
          this.$refs.fromInput.value = null;
          this.$refs.toInput.value = null;
        }
      }
    },
  },
  data() {
    return {
      invalid: false,
      clickNumber: 0,
    };
  },
};
</script>

<style scoped>
h3 {
  font-family: "Russo One", sans-serif;
  margin-top: 20px;
}

.row {
  max-width: 300px;
  margin: auto;
}

button {
  margin-top: 20px;
  font-family: "Russo One", sans-serif;
  background-color: transparent;
  border-style: solid;
  border-radius: 5px;
  border-width: 4px;
  border-color: black;
  padding: 5px;
  font-size: 24px;
}

button:hover {
  background-color: black;
  color: white;
}
</style>
