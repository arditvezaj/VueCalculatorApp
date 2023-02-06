<script setup>
import { ref } from "vue";

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
      <div>
        <button @click="input = ''" class="extra-operators">C</button>
        <button @click="input = '-' + input" class="extra-operators">
          +/-
        </button>
        <button @click="input += '%'" class="extra-operators">%</button>
        <button @click="input += '/'" class="operators">÷</button>
      </div>

      <div>
        <button @click="input += '7'">7</button>
        <button @click="input += '8'">8</button>
        <button @click="input += '9'">9</button>
        <button @click="input += '*'" class="operators">x</button>
      </div>

      <div>
        <button @click="input += '4'">4</button>
        <button @click="input += '5'">5</button>
        <button @click="input += '6'">6</button>
        <button @click="input += '-'" class="operators">-</button>
      </div>

      <div>
        <button @click="input += '1'">1</button>
        <button @click="input += '2'">2</button>
        <button @click="input += '3'">3</button>
        <button @click="input += '+'" class="operators">+</button>
      </div>

      <div>
        <button @click="input += '0'" id="zero">0</button>
        <button @click="input += '.'">,</button>
        <button
          @click="`${calculate()} && ${(input += '=' + result)}`"
          class="operators"
        >
          =
        </button>
      </div>
    </section>
  </body>
</template>

<style scoped>
body {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

section {
  background-color: rgb(41, 40, 40);
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

@media (max-width: 49rem) {
  input {
    width: 90%;
    height: 5rem;
    font-size: 1.6rem;
  }

  button {
    font-size: 1.5rem;
    width: 4.5rem;
    height: 4.5rem;
    margin: 0.3rem;
  }

  #zero {
    width: 9.5rem;
  }
}
</style>
