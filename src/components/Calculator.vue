<template>
  <div class="card">
    <div class="output-screen">{{secondOperand || firstOperand}}</div>
   <div class='button-container'>

     <div class="row">
       <button @click="clear()" class="clear">c</button>
     </div>
     <div class="row">
       <button @click="appendChar(1)">1</button>
       <button @click="appendChar(2)">2</button>
       <button @click="appendChar(3)">3</button>
       <button class="ops" @click="operater='+'">+</button>
     </div>

     <div class="row">
       <button @click="appendChar(4)">4</button>
       <button @click="appendChar(5)">5</button>
       <button @click="appendChar(6)">6</button>
       <button class="ops" @click="operater='-'">-</button>
     </div>

     <div class="row">
       <button @click="appendChar(7)">7</button>
       <button @click="appendChar(8)">8</button>
       <button @click="appendChar(9)">9</button>
       <button class="ops" @click="operater='*'">x</button>
     </div>

     <div class="row">
       <button @click="appendChar(0)">0</button>
       <button @click="appendChar('.')">.</button>
       <button @click="eval">=</button>
       <button class="ops" @click="operater='/'">/</button>
     </div>

   </div>
  </div>
</template>

<script>
  export default {
    name:"Calculator",
    data(){
      return{
        firstOperand:'',
        secondOperand:'',
        operater:''
      }
    },
    methods:{
      eval(){
        const {firstOperand, secondOperand, operater} = this
        this.firstOperand = eval(firstOperand + operater + secondOperand).toString()
        this.secondOperand = ''
        this.operater = ''
      },
      appendChar(char){
        let currentOperand = this.operater ? 'secondOperand':'firstOperand'
        if(char=='.'){
          if(this[currentOperand].indexOf('.') == -1){
            this[currentOperand] += char
          }
        }else{
           this[currentOperand] += char
        }
        
      },
      clear(){
        this.firstOperand = '',
        this.secondOperand = '',
        this.operator = ''
      }
    }
  }
</script>

<style scoped>
button{
  padding: 15px;
  width:4rem;
  height: 4rem;
  border: 0.5px solid black;
  background-color: rgb(63, 62, 62);
  outline: none;

}
button.ops{

  background-color: rgb(241, 234, 16);

}
.clear{
  background-color: rgb(241, 234, 16);
  font-size: 2rem;
  text-emphasis:bold;
  width: fill-available;
}
.output-screen{
  background-color: #ccc;
  width: 256px;
  overflow: hidden;
  height: 3.5rem;
  font-size: 3rem;
}
.row{
  display: flex;
}
.card{
  margin-top:4rem;
  padding:0%;
  border: 1px solid black;
  width: fit-content;
}
</style>