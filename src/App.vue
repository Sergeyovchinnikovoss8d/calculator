<template>
  <div id="app">
   <input v-model="display" type="number">
   <div class="buttons">
      <button @click="plus">+</button>
      <button @click="minus">-</button>
      <button @click="calculate">=</button>
      <button @click="clear">c</button>
      <button @click="divide">/</button>
      <button @click="multiply">*</button>
      <button v-for="n in 10" :key="n" @click="inputnumber(n-1)">{{n-1}}</button>
      
   </div>
   <p>display:{{display}} first:{{first}} operation:{{operation}}</p>
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
      if(this.operation==='/'){
        this.display=Number(this.first)/Number(this.display)
        this.operation=''
        this.first=0
      }
      if(this.operation==='*'){
        this.display=Number(this.first)*Number(this.display)
        this.operation=''
        this.first=0
      }
    },
    inputnumber(n){
      if (this.display==="0")
        this.display=String(n)
      else 
       this.display+=n
    },
    divide(){
      this.first=this.display
      this.display="0"
      this.operation="/"
    },
    multiply(){
      this.first=this.display
      this.display="0"
      this.operation="*"
    },
  }

}
</script>

<style>
body{background-color: aqua;}
.buttons{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
.buttons>button{
  height: 70px;
  font-size: 30px;
  background-color: #8ce2f5;
  border-radius: 15px;
}
input{
  height:50px;
  font-size:30px;
  width: 492px;
  margin-bottom: 25px;
  background-color: #b2ebf7;
  border-radius: 15px;
}
#app {
  background: rgb(22,102,136);
  background: linear-gradient(0deg, rgba(22,102,136,1) 0%, rgba(132,243,252,1) 61%, rgba(0,212,255,1) 100%);
  max-width: 500px;
  margin: auto;
  margin-top: 60px;
  font-size:30px;
  color: white;
}
</style>
