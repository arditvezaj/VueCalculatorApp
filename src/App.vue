<script setup></script>

<template>
  <body>
    <div>
      <button class="extra-operators">AC</button>
      <button class="extra-operators">+/-</button>
      <button class="extra-operators">%</button>
      <button class="operators">÷</button>
    </div>

    <div>
      <button>7</button>
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
      <button class="operators">=</button>
    </div>
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
</style>
