<template>
  <div class="calculator">
    <!-- Calculator display-->
    <div class="display">{{displayValue}}</div>
    <!-- Calculator buttons -->
    <button v-for="button in buttons" :key="button" @click="handleClick(button)">{{button}}</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      displayValue: '0',
      buttons: ['AC', 'CE', '%', '/', 7, 8, 9, '*', 4, 5, 6, '-', 1, 2, 3, '+', 0, '.', '√', '=']
    }
  },
  methods: {
    // This method is called when a button is clicked
    handleClick(value) {
      // If the value is a number, add it to the display value
      if (!isNaN(value)) {
        this.displayValue += value;
      }
      // If the value is "AC", reset the display value to 0
      else if (value === 'AC') {
        this.displayValue = '0';
      }
      // If the value is "CE", remove the last character from the display value
      else if (value === 'CE') {
        this.displayValue = this.displayValue.slice(0, -1);
      }
      // If the value is "√", calculate the square root of the display value and update the display value with the result
      else if (value === '√') {
        this.displayValue = Math.sqrt(this.displayValue);
      }
      // If the value is "=", evaluate the display value as an expression and update the display value with the result
      else if (value === '=') {
        this.displayValue = eval(this.displayValue);
      }
      // If the value is any of the other buttons, add them to the display value
      else {
        this.displayValue += value;
      }
    }
  }
}
</script>


<style>
/* Style for the calculator */
.calculator {
  display: flex;
  flex-wrap: wrap;
  width: 240px;
  height: 390px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

/* Style for the calculator's display */
.display {
  width: 100%;
  height: 80px;
  background-color: #eee;
  border-bottom: 1px solid #666;
  font-size: 24px;
  text-align: right;
  padding: 20px;
  box-sizing: border-box;
}

/* Style for the calculator's buttons */
.calculator button {
  width: 25%;
  height: 60px;
  background-color: white;
  border: 1px solid #666;
  font-size: 18px;
  cursor: pointer;
}
</style>