<script>

import "bootstrap/dist/css/bootstrap.min.css"
import "bootstrap"
export default {
  data() {
    return {
      equation: "",
      display: "",
      operatorClicked: ""
    };

  },
  methods: {
    onClick(val) {
      if (val === "=") {
        this.calculate();
      } else if (this.equation.at(-1) === '(') {
        this.equation += val;
        this.equation += ')';
        this.display = this.equation;
      } else {
        this.equation += val;
        this.display += val;
      }
    },
    calculate() {
      try {
        this.equation = eval(this.equation).toString();
        this.display = this.equation;
      } catch (e) {
        this.display = "Error";
      }
      this.equation = "";
    },
    clear() {
      this.equation = "";
      this.display = "";
    },
    clearEntry() {
      this.display = "";
    },
  }
}

</script>

<template>
  <div class="d-flex align-items-start flex-column mt-5 mx-auto p-3 border rounded justify-content-between">
    <p>{{ display }}</p>
    <div class="d-flex m-1 justify-content-between">
      <button class="btn btn-success" @click="onClick('%')">%</button>
      <button class="btn btn-success" @click="onClick('Math.sqrt(')">√</button>
      <button class="btn btn-success" @click="clearEntry">CE</button>
      <button class="btn btn-success" @click="clear">C</button>
    </div>
    <div class="d-flex m-1 justify-content-between">
      <button class="btn btn-success" @click="onClick('7')">7</button>
      <button class="btn btn-success" @click="onClick('8')">8</button>
      <button class="btn btn-success" @click="onClick('9')">9</button>
      <button class="btn btn-success" @click="onClick('/')">÷</button>
    </div>
    <div class="d-flex m-1">
      <button class="btn btn-success" @click="onClick('4')">4</button>
      <button class="btn btn-success" @click="onClick('5')">5</button>
      <button class="btn btn-success" @click="onClick('6')">6</button>
      <button class="btn btn-success" @click="onClick('*')">×</button>
    </div>
    <div class="d-flex m-1">
      <button class="btn btn-success" @click="onClick('1')">1</button>
      <button class="btn btn-success" @click="onClick('2')">2</button>
      <button class="btn btn-success" @click="onClick('3')">3</button>
      <button class="btn btn-success" @click="onClick('-')">-</button>
    </div>
    <div class="d-flex m-1">
      <button class="btn btn-success" @click="onClick('0')">0</button>
      <button class="btn btn-success" @click="onClick('.')">.</button>
      <button class="btn btn-success" @click="calculate">=</button>
      <button class="btn btn-success" @click="onClick('+')">+</button>
    </div>
  </div>


</template>

<style>
.calculator {
  width: 300px;
  height: 400px;
  background: #8ac6d0;
  border-radius: 10px;
  padding: 20px;
  margin: 100px auto;
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
}

.display {
  width: 100%;
  height: 50px;
  background: #324a5e;
  color: white;
  text-align: right;
  font-size: 2em;
  line-height: 50px;
  padding-right: 10px;
  box-sizing: border-box;
  border-radius: 5px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
  margin-top: 20px;
}

.button {
  width: 100%;
  height: 50px;
  background: #2b3a42;
  color: white;
  font-size: 1.5em;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.button.operation {
  background: #2a4d69;
}

.button.double {
  grid-column: span 2;
}
</style>
