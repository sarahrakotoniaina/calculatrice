<template>
    <div id="app" class="calculator">
      <div class="display">
        <input type="text" v-model="inputStr" class="input-display" disabled />
      </div>
  
      <div class="buttons">
        <div class="row">
          <div class="col-auto">
            <button class="btn operator" @click="appendToInput('+')">+</button>
            <button class="btn operator" @click="appendToInput('-')">-</button>
            <button class="btn operator" @click="appendToInput('/')">/</button>
            <button class="btn operator" @click="appendToInput('*')">*</button>
            <button class="btn" @click="appendToInput('(')">(</button>
            <button class="btn" @click="appendToInput(')')">)</button>
          </div>
        </div>
  
        <div class="row">
          <div class="col-auto">
            <button class="btn number" @click="appendToInput('7')">7</button>
            <button class="btn number" @click="appendToInput('8')">8</button>
            <button class="btn number" @click="appendToInput('9')">9</button>
            <button class="btn operator" @click="appendToInput('^')">^</button>
          </div>
        </div>
  
        <div class="row">
          <div class="col-auto">
            <button class="btn number" @click="appendToInput('4')">4</button>
            <button class="btn number" @click="appendToInput('5')">5</button>
            <button class="btn number" @click="appendToInput('6')">6</button>
            <button class="btn operator" @click="appendToInput('sqrt(')">√</button>
          </div>
        </div>
  
        <div class="row">
          <div class="col-auto">
            <button class="btn number" @click="appendToInput('1')">1</button>
            <button class="btn number" @click="appendToInput('2')">2</button>
            <button class="btn number" @click="appendToInput('3')">3</button>
            <button class="btn clear" @click="clearInput">C</button>
            <button class="btn number" @click="appendToInput('0')">0</button>
            <button class="btn equal" @click="calculateResult">=</button>
          </div>
        </div>
  
        <div class="row">
          <div class="col-auto">
            <button class="btn function" @click="appendToInput('Math.sin(')">sin</button>
            <button class="btn function" @click="appendToInput('Math.cos(')">cos</button>
            <button class="btn function" @click="appendToInput('Math.log(')">log</button>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'App',
    data() {
      return {
        inputStr: ''
      };
    },
    methods: {
      appendToInput(character) {
        this.inputStr += character;
      },
      calculateResult() {
        try {
          this.inputStr = eval(this.inputStr);
        } catch (error) {
          this.inputStr = 'Syntax Error';
        }
      },
      clearInput() {
        this.inputStr = '';
      }
    }
  };
  </script>
  
  <style scoped>
  
  .calculator {
    width: 300px;
    background-color: #f2f2f2;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    padding: 20px;
  }
  
  .display {
    margin-bottom: 20px;
  }
  
  .input-display {
    width: 100%;
    height: 60px;
    font-size: 24px;
    text-align: right;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #fff;
  }
  
  .buttons .row {
    margin-bottom: 10px;
  }
  
  .buttons .col-auto {
    display: flex;
    justify-content: space-between;
  }
  
  .btn {
    width: calc(25% - 5px);
    height: 50px;
    font-size: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  .btn:hover {
    background-color: #ddd;
  }
  
  .operator {
    background-color: burlywood;
    color: #fff;
  }
  
  .number {
    background-color: #f2f2f2;
  }
  
  .clear {
    background-color: burlywood;
    color: #fff;
  }
  
  .equal {
    background-color: burlywood;
    color: #fff;
  }
  
  .function {
    background-color: burlywood;
    color: #fff;
  }
  </style>
  
