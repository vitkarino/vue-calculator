<script>
import { ref } from 'vue'

export default {
  name: 'CalculatorComponent',
  setup() {
    const inputNumber = ref('')
    const total = ref(0)
    const currentOperation = ref(null)

    function addToOutput(value) {
      if (value === '.') {
        if (!inputNumber.value.includes('.')) {
          inputNumber.value += '.'
        }
      } else {
        inputNumber.value += value
      }
    }

    function clearOutput() {
      inputNumber.value = ''
      total.value = 0
      currentOperation.value = null
    }

    function performOperation(op = null) {
      const inputVal = inputNumber.value ? parseFloat(inputNumber.value) : 0
      if (!currentOperation.value && op !== '=') {
        currentOperation.value = op
        total.value = inputVal
        inputNumber.value = ''
      } else if (currentOperation.value) {
        switch (currentOperation.value) {
          case '+':
            total.value += inputVal
            break
          case '-':
            total.value -= inputVal
            break
          case '/':
            total.value /= inputVal
            break
          case '*':
            total.value *= inputVal
            break
        }
        inputNumber.value = op === '=' ? total.value.toString() : ''
        currentOperation.value = op !== '=' ? op : null
      }
    }

    function showResult() {
      performOperation('=')
    }

    return { inputNumber, total, addToOutput, clearOutput, performOperation, showResult }
  }
}
</script>

<template>
  <div class="calculator">
    <table>
      <tr>
        <td colspan="3"><input type="text" id="result" v-model="inputNumber" /></td>
        <td><input type="button" value="c" @click="clearOutput()" /></td>
      </tr>
      <tr>
        <td><input type="button" value="1" @click="addToOutput('1')" /></td>
        <td><input type="button" value="2" @click="addToOutput('2')" /></td>
        <td><input type="button" value="3" @click="addToOutput('3')" /></td>
        <td><input type="button" value="/" @click="performOperation('/')" /></td>
      </tr>
      <tr>
        <td><input type="button" value="4" @click="addToOutput('4')" /></td>
        <td><input type="button" value="5" @click="addToOutput('5')" /></td>
        <td><input type="button" value="6" @click="addToOutput('6')" /></td>
        <td><input type="button" value="*" @click="performOperation('*')" /></td>
      </tr>
      <tr>
        <td><input type="button" value="7" @click="addToOutput('7')" /></td>
        <td><input type="button" value="8" @click="addToOutput('8')" /></td>
        <td><input type="button" value="9" @click="addToOutput('9')" /></td>
        <td><input type="button" value="-" @click="performOperation('-')" /></td>
      </tr>
      <tr>
        <td><input type="button" value="0" @click="addToOutput('0')" /></td>
        <td><input type="button" value="." @click="addToOutput('.')" /></td>
        <td><input type="button" value="=" @click="showResult()" /></td>
        <td><input type="button" value="+" @click="performOperation('+')" /></td>
      </tr>
    </table>
  </div>
</template>

<style scoped lang="scss">
@import '/src/assets/main.scss';

table {
  margin-left: auto;
  margin-right: auto;

  input[type='button'] {
    width: 7vh;
    height: 7vh;
    background: none;
    color: $text-light;
    font-size: 24px;
    font-weight: bold;
    transition: 0.1s ease-in-out;
    border: none;

    &:hover {
      filter: brightness(1.3);
      cursor: pointer;
    }
  }

  input[type='text'] {
    max-width: calc(3 * 7vh + 6px);
    height: 7vh;
    font-size: 24px;
    font-weight: bold;
    outline: none;
    border: none;
    color: $text-light;
    padding: 20px;
    background-color: #292929;
    transition: 0.1s ease-in-out;

    &:focus {
      filter: brightness(1.3);
    }
  }
}
</style>
