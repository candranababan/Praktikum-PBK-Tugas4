<template>
  <div class="calculator">
    <h1>Calculator</h1>
    <div class="display">{{ current }}</div>
    <div class="buttons">
      <CalcButton value="C" @click="clear" />
      <CalcButton value="/" @click="append" />
      <CalcButton value="*" @click="append" />
      <CalcButton value="-" @click="append" />
      <CalcButton value="7" @click="append" />
      <CalcButton value="8" @click="append" />
      <CalcButton value="9" @click="append" />
      <CalcButton value="+" @click="append" />
      <CalcButton value="4" @click="append" />
      <CalcButton value="5" @click="append" />
      <CalcButton value="6" @click="append" />
      <CalcButton value="1" @click="append" />
      <CalcButton value="2" @click="append" />
      <CalcButton value="3" @click="append" />
      <CalcButton value="0" @click="append" />
      <CalcButton value="." @click="append" />
      <CalcButton value="=" @click="calculate" />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import CalcButton from "@/components/Calcbutton.vue";

const current = ref("");

const append = (char) => {
  current.value += char;
};

const clear = () => {
  current.value = "";
};

const calculate = () => {
  try {
    current.value = eval(current.value).toString();
  } catch (error) {
    current.value = "Error";
  }
};
</script>

<style scoped>
.calculator {
  justify-content: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px;
}
.display {
  width: 220px;
  height: 50px;
  background: #eee;
  text-align: right;
  padding: 10px;
  font-size: 1.5em;
  margin-bottom: 10px;
}
.buttons {
  display: grid;
  grid-template-columns: repeat(4, 60px);
  grid-gap: 10px;
}
</style>
