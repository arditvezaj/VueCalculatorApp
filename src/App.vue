<script setup>
import { ref, computed } from "vue";

const input = ref("");
const result = computed(() => {
  try {
    return eval(input.value);
  } catch (error) {
    return error.message;
  }
});

const clearInput = () => {
  input.value = "";
};

const changeSign = () => {
  if (input.value[0] === "-") {
    input.value = input.value.substring(1);
  } else {
    input.value = "-" + input.value;
  }
};

const preventCharacters = () => {
  const validChars = /^[0-9+\-*/.]+$/;
  if (!validChars.test(input.value)) {
    input.value = input.value.slice(0, -1);
  }
};

const addOperator = (operator) => {
  input.value += operator;
};

const addInput = (num) => {
  input.value += num;
};

const calculateResult = () => {
  if (isNaN(result.value)) {
    input.value = result.value;
  } else {
    result.value = eval(input.value);
  }
};
</script>

<template>
  <body>
    <section>
      <input v-model="input" type="type" @input="preventCharacters" />
      <div>
        <button @click="clearInput" class="extra-operators">C</button>
        <button @click="changeSign" class="extra-operators">+/-</button>
        <button @click="addOperator('%')" class="extra-operators">%</button>
        <button @click="addOperator('/')" class="operators">÷</button>
      </div>

      <div>
        <button @click="addInput('7')">7</button>
        <button @click="addInput('8')">8</button>
        <button @click="addInput('9')">9</button>
        <button @click="addOperator('*')" class="operators">x</button>
      </div>

      <div>
        <button @click="addInput('4')">4</button>
        <button @click="addInput('5')">5</button>
        <button @click="addInput('6')">6</button>
        <button @click="addOperator('-')" class="operators">-</button>
      </div>

      <div>
        <button @click="addInput('1')">1</button>
        <button @click="addInput('2')">2</button>
        <button @click="addInput('3')">3</button>
        <button @click="addOperator('+')" class="operators">+</button>
      </div>

      <div>
        <button @click="addInput('0')" id="zero">0</button>
        <button @click="addOperator('.')">,</button>
        <button
          @click="`${calculateResult()} && ${(input = result)}`"
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
  text-align: end;
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

button:hover {
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

@media (max-width: 48rem) {
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
