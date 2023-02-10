<template>
  <div id="home" class="home">
    <img src="./assets/pkbfechada.png"/>
    PokeFind
    <div class="byside">
    <input type="text" placeholder="digite aqui" v-on:change="search" />
    <div class="icon" v-on:click="doSearch"><ion-icon name="search-outline"></ion-icon></div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
let pokenome="";
export default({
  el: "#home",
  name: 'App',
  methods:{
    search: function(event){
      pokenome=(event.target.value);
    },
    doSearch: function(){
      if(pokenome===""){
        alert("invalido");
      }else{
        axios
          .get(`https://pokeapi.co/api/v2/pokemon/${pokenome}`)
          .then(response=>{
            console.log(response);
          })
          .catch(error=>{
            console.log(error);
          })
      }
    }
  }
})
</script>

<style>
#app {
  color: red;
  font-size: 80px;
  margin-top: 60px;
}
.home{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}
.icon{
  display: flex;
  align-items: center;
  font-size: 38px;
  color: blue;
}
input{
  border-radius: 30px;
  border: 2px solid blue;
  width: 300px;
  padding: 10px;
}
.byside{
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
