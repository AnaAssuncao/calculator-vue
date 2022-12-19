<template>
  <div class="calculator">
    <Display :value= "displayValue? displayValue : '0'" > </Display>
    <Button label="AC" triple @onClick="clearMemory" > </Button>
    <Button label="/" operation @onClick="setOperation"> </Button>
    <Button label="7" @onClick="addDigit"> </Button>
    <Button label="8" @onClick="addDigit"> </Button>
    <Button label="9" @onClick="addDigit"> </Button>
    <Button label="*" operation @onClick="setOperation"> </Button>
    <Button label="4" @onClick="addDigit"> </Button>
    <Button label="5" @onClick="addDigit"> </Button>
    <Button label="6" @onClick="addDigit"> </Button>
    <Button label="-" operation @onClick="setOperation"> </Button>
    <Button label="1" @onClick="addDigit"> </Button>
    <Button label="2" @onClick="addDigit"> </Button>
    <Button label="3" @onClick="addDigit"> </Button>
    <Button label="+" operation @onClick="setOperation"> </Button>
    <Button label="0" double @onClick="addDigit"> </Button>
    <Button label="." @onClick="addDigit"> </Button>
    <Button label="=" operation @onClick="setOperation"> </Button>
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