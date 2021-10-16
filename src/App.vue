<template>
  <div id="app">
    <h3>Cadastro</h3>
    <small id="deuErro" v-show="deuErro1">Nome inválido tente novamente!</small><br>
    <input type="text" placeholder="nome" v-model="nomeField"/><br>
    <small id="deuErro" v-show="deuErro2">Idade inválida tente novamente!</small><br>
    <input type="number" placeholder="idade" v-model="idadeField"/><br>
    <small id="deuErro" v-show="deuErro3">Email inválido tente novamente!</small><br>
    <input type="text" placeholder="email" v-model="emailField"/><br>
    <input @click="gravar()" type="submit" value="Cadastrar">    
    
    <hr>

    <div v-for="cliente in clientes" :key="cliente.id" >
          <Cliente :cliente="cliente"/>
    </div>

  </div>
  <router-view/>
</template>


<script>
import Cliente from './components/Cliente.vue';


export default {
  name: 'App',
    data(){
      return{
        deuErro1: false,
        deuErro2: false,
        deuErro3: false,
        nomeField:'',
        idadeField:0,
        emailField:'',

        clientes: [
          {id:1, nome:'Albert Einsten', idade:50, email:'alberteinsten@gmail.com'},
          {id:2, nome:'Nikola Tesla', idade:45, email:'nikolatesla@gmail.com'},
          {id:3, nome:'Grace Hopper', idade:40, email:'gracehopper@gmail.com'}
        ]
        }
    },
  components:{
    Cliente
  },
  methods:{
    gravar: function(){
      if(this.nomeField === ''|| this.nomeField === ' ' || this.nomeField === undefined){
        this.deuErro1 = true;
      }else if(this.idadeField <= 0){
        this.deuErro2 = true;
      }else if(this.emailField === ''|| this.emailField === ' ' || this.emailField === undefined){
        this.deuErro3 = true;
      }else{
        this.clientes.push({nome:this.nomeField, idade:this.idadeField, email:this.emailField, id:Date.data})
        this.nomeField ='';
        this.idadeField ='';
        this.emailField ='';
        this.deuErro1 = false;
        this.deuErro2 = false;
        this.deuErro3 = false;
      }
    }      
  }
}
</script>

<style>
  #app{
    width: 100%;
  }
  #app input{
    padding: 10px;
    width: 300px;
  }
  #deuErro{
    color: red;
  }
</style>


