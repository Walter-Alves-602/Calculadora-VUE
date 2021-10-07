<template>
  <div class="calculator">
      <Display :value="displayValue" />
      <Button label="clear" triple @batatinha ="clearMemory" />
      <Button label="/" operation @batatinha ="setOperation" />
      <Button label="7" @batatinha ="addDigit" />
      <Button label="8" @batatinha ="addDigit" />
      <Button label="9" @batatinha ="addDigit" />
      <Button label="*" operation @batatinha ="setOperation" />
      <Button label="4" @batatinha ="addDigit" />
      <Button label="5" @batatinha ="addDigit" />
      <Button label="6" @batatinha ="addDigit" />
      <Button label="-" operation @batatinha ="setOperation" />
      <Button label="1" @batatinha ="addDigit" />
      <Button label="2" @batatinha ="addDigit" />
      <Button label="3" @batatinha ="addDigit" />
      <Button label="+" operation @batatinha ="setOperation" />
      <Button label="0" double @batatinha ="addDigit" />
      <Button label="." @batatinha ="addDigit" />
      <Button label="=" operation @batatinha ="setOperation" />
      
  </div>
</template>

<script>
import Display from "../components/Display.vue"
import Button from "../components/Button.vue"

export default {
  data: function(){
    return{
      displayValue: "0",
      clearDisplay: false,
      operation: null,
      values: [0, 0],
      current: 0
    }
  },

  components: {Button, Display},
  methods: {
     clearMemory(){
       Object.assign(this.$data, this.$options.data())
     },
     setOperation(operation){
       if (this.current === 0) {
                this.operation = operation
                this.current = 1
                this.clearDisplay = true
            } else {
                const equals = operation === "="
                const currentOperation = this.operation

                try {
                  console.log(`${this.values[0]} ${currentOperation} ${this.values[1]}`)
                    this.values[0] = eval(
                        `${this.values[0]} ${currentOperation} ${this.values[1]}`
                    )
                } catch (e) {
                    this.$emit('onError', e)
                }

                this.values[1] = 0

                this.displayValue = this.values[0]
                this.operation = equals ? null : operation
                this.current = equals ? 0 : 1
                this.clearDisplay = !equals
            }
        },
     addDigit(n){
       if (n === "." && this.displayValue.includes(".")) {
                return
            }

            const clearDisplay = this.displayValue === "0"
                || this.clearDisplay
            const currentValue = clearDisplay ? "" : this.displayValue
            const displayValue = currentValue + n

            this.displayValue = displayValue
            this.clearDisplay = false
            
            if (n !== ".") {
               const i = this.current
               const newValue = parseFloat(displayValue)
               this.values[i] = newValue
            }
      }
   } 
}

</script>

<style>
.calculator {
    height: 320px;
    width: 235px;
    border-radius: 10px;
    overflow: hidden;

    display: grid;
    grid-template-columns: repeat(4, 25%);
    grid-template-rows: 1fr 48px 48px 48px 48px 48px;
    background-color:#97A6AC ;
    padding: 5px;
    box-shadow: 5px 5px 4px #00000050;
}
</style>