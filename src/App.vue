<script setup>
import { ref, computed } from "vue";

let input = ref("");
const result = ref(0);

const calculate = () => {
  result.value = eval(input.value);
};

</script>

<template>
  <body>
    <section>
      <input v-model="input" type="text" />
      <div id="result">{{ result }}</div>
      <div>
        <button @click="`${input = ''}`" class="extra-operators">AC</button>
        <button class="extra-operators">+/-</button>
        <button class="extra-operators">%</button>
        <button class="operators">÷</button>
      </div>

      <div>
        <button @click="input.innerText= '+'">7</button>
        <button>8</button>
        <button>9</button>
        <button class="operators">x</button>
      </div>

      <div>
        <button>4</button>
        <button>5</button>
        <button>6</button>
        <button class="operators">-</button>
      </div>

      <div>
        <button>1</button>
        <button>2</button>
        <button>3</button>
        <button class="operators">+</button>
      </div>

      <div>
        <button id="zero">0</button>
        <button>,</button>
        <button @click="calculate" class="operators">=</button>
      </div>
    </section>
  </body>
</template>

<style scoped>
body {
  background-color: rgb(41, 40, 40);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

section {
  border: 2px solid rgb(234, 234, 76);
  border-radius: 1rem;
}

input {
  width: 32rem;
  height: 6rem;
  margin: 2rem 1rem;
  border-radius: 5px;
  border: none;
  font-size: 3rem;
}

div {
  margin-left: 1rem;
  margin-right: 1rem;
}

button {
  font-size: 2.5rem;
  width: 7rem;
  height: 7rem;
  margin: 0.5rem;
  color: rgb(0, 0, 0);
  background-color: rgb(164, 164, 164);
  border-radius: 100%;
  border: none;
  cursor: pointer;
}

button:hover,
button:active {
  background-color: rgb(225, 209, 138);
}
.extra-operators {
  background-color: rgb(66, 66, 64);
  color: white;
}
.operators {
  background-color: rgb(239, 195, 53);
  color: white;
  font-weight: bold;
}

#zero {
  width: 15rem;
  border-radius: 5rem;
}

#result {
  width: 15rem;
  height: 4rem;
  background-color: white;
  margin-left: 18rem;
  font-size: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
}
</style>
