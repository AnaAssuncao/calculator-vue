<template>
  <div class="calculator">
    <Display :value= "displayValue? displayValue : '0'" > </Display>
    <Button label="AC" triple @testeClick="clearMemory" > </Button>
    <Button label="/" operation @testeClick="setOperation"> </Button>
    <Button label="7" @testeClick="addDigit"> </Button>
    <Button label="8" @testeClick="addDigit"> </Button>
    <Button label="9" @testeClick="addDigit"> </Button>
    <Button label="*" operation @testeClick="setOperation"> </Button>
    <Button label="4" @testeClick="addDigit"> </Button>
    <Button label="5" @testeClick="addDigit"> </Button>
    <Button label="6" @testeClick="addDigit"> </Button>
    <Button label="-" operation @testeClick="setOperation"> </Button>
    <Button label="1" @testeClick="addDigit"> </Button>
    <Button label="2" @testeClick="addDigit"> </Button>
    <Button label="3" @testeClick="addDigit"> </Button>
    <Button label="+" operation @testeClick="setOperation"> </Button>
    <Button label="0" double @testeClick="addDigit"> </Button>
    <Button label="." @testeClick="addDigit"> </Button>
    <Button label="=" operation @testeClick="setOperation"> </Button>
  </div>
  
</template>

<script>
import Button from './Button.vue';
import Display from './Display.vue';

export default {
  data () {
    return{
      displayValue:"",
      values:[],
      numberCurret:""
    }
  },
  components:{
    Button,
    Display
  },
  methods:{
    clearMemory(){
      this.displayValue=""
    },
    setOperation(label){
      if(label === "="){
        try{
          const operation = eval(this.displayValue)
          this.displayValue = operation
        return
        }catch (e) {
          this.displayValue = "Expressão mal formada"
          return
         }
      }
      this.displayValue=this.displayValue+label
      this.numberCurret=""
    },
    addDigit(label){
      if(label=== "." && this.numberCurret.includes('.')){
        return
      }
      this.numberCurret=this.displayValue+label
      this.displayValue=this.displayValue+label
    },
  }
}
</script>

<style>
.calculator {
    height: 320px;
    width: 235px;
    border-radius: 5px;
    overflow: hidden;
    display: grid;
    grid-template-columns: repeat(4, 25%);
    grid-template-rows: 1fr 48px 48px 48px 48px 48px;
    margin: auto;
}
</style>