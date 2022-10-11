<template>
  <div id="app">
   <input v-model="display" type="number">
   <div class="buttons">
      <button @click="plus">+</button>
      <button @click="minus">-</button>
      <button @click="calculate">=</button>
      <button @click="clear">c</button>
      <button v-for="n in 10" :key="n" @click="inputnumber(n-1)">{{n-1}}</button>
      <p>display:{{display}} first:{{first}} operation:{{operation}}</p>
   </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      display: "0",
      first: "0",
      operation: ""
    }
  },
  methods:{
    plus(){
      this.first=this.display
      this.display="0"
      this.operation="+"
    },
    minus(){
      this.first=this.display
      this.display="0"
      this.operation="-"
    },
    clear(){
      this.first="0"
      this.display="0"
      this.operation=''
    },
    calculate(){
      if(this.operation==='+'){
        this.display=Number(this.display)+Number(this.first)
        this.operation=''
        this.first=0
      }
      if(this.operation==='-'){
        this.display=Number(this.first)-Number(this.display)
        this.operation=''
        this.first=0
      }
    },
    inputnumber(n){
      if (this.display==="0")
        this.display=String(n)
      else 
       this.display+=n
    }
  }

}
</script>

<style>
.buttons{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
.buttons>button{
  height: 65px;
  font-size: 30px;
}
input{
  height:50px;
  font-size:30px;
  width: 100%;
  margin-bottom: 25px;
}
#app {
  max-width: 450px;
  margin:auto;
  margin-top: 60px;
}
</style>
