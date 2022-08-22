<template>
  <div id="app">
    <div class="calculator">
      <div class="calc" :value="calc">{{calc}}</div>
      <div class="value"> {{value}}</div>
      <div class="buttons">
        <div v-for="x in 10"  @click="setModifier(x)"  class="btn">{{ x-1 }}</div>
        <div @click="add()" class="btn">+</div>
        <div @click="substract()" class="btn">-</div>
        <div @click="divide()" class="btn">/</div>
        <div @click="multiply()" class="btn">*</div>
        <div @click="calculate()" class="btn">=</div>
        <div @click="reset()" class="btn">C</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  components: {
    name: 'app'
  },
  data() {
    return {
      calc: '',
      value: null
    }
  },
  methods: {
    add() {
      this.calc += '+'
    },
    substract() {
      this.calc += '-'
    },
    divide() {
      this.calc += '/'
    },
    multiply() {
      this.calc += '*'
    },
    setModifier(x) {
      this.calc += x - 1
    },
    calculate() {
      this.value = eval(this.calc)
      // this.calc += this.value
    },
    reset() {
      this.value = null
      this.calc = ''
    }
  },
  watch: {
    calc(value) {
      if (value.length > 10 || value === '0') {
        this.calc = ''
      }
    }
  }
}
</script>
<style>
body {
  background-color: black;
  background-size: cover;
  color: rgba(255, 255, 255, 0.5);
  width: 100vw;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 20px;
  text-align: center;
}

.calculator {
  width: 320px;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 5px;
  padding: 20px;
}

.buttons {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  width: 320px;
}

.btn {
  flex: 0 0 93px;
  height: 63px;
  border: 1px solid transparent;
  line-height: 61px;
  transition: all 0.8s;
  border-radius: 3px;
}

.btn:hover {
  background-color: rgba(255, 255, 255, 0.5);
  border-color: rgba(255, 255, 255, 0.2);
  color: white;
  cursor: pointer;
  transition: all 0.25s;
}

.calc {
  height: 30px;
  line-height: 30px;
}

.value {
  height: 50px;
  line-height: 50px;
  color: white;
  font-size: 30px;
}

</style>
