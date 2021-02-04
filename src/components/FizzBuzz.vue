<template>
  <div>
    <ul>
      <li
        :class="n === 'fizz buzz' ? 'fizzbuzz' : n"
        v-for="(n, i) in fizzBuzz"
        :key="i"
      >
        {{ n }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["fizzBuzz"],
};
</script>

<style scoped>
ul {
  margin-top: 15px;
  max-width: 500px;
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

li:hover {
  transform: scale(0.9);
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
</style>
