<template>
    <div :class="{'cliente': !isPremium, 'cliente-premium':isPremium}">
        <h2>Cliente: {{cliente.nome}}</h2>
        <p><strong>Idade:</strong> {{cliente.idade}}</p>
         <!-- <p v-if="showIdade === true"><strong>Idade:</strong> {{cliente.idade}}</p> -->
        <!-- <p v-else><strong>O usuário escondeu a idade</strong></p> -->
        <p><strong>Email:</strong> {{cliente.email}} </p>
        <button @click="mudarCor($event)">Mudar Cor</button>
    </div>
</template>

<script>
export default {
    data(){
        return{
            isPremium: false
        }
    },
    props:{
        cliente: Object
    },
    methods:{
        mudarCor: function($event){
            console.log($event);
            this.isPremium = !this.isPremium;
        }
    }
}
</script>

<style>
    .cliente{
        width: 450px;
        display: flex;
        flex-direction: column;
        padding: 20px;
        margin-top: 10px;
        border: 1px solid gray;
    }
    .cliente-premium{
        background-color: black;
        color: goldenrod;

        width: 450px;
        display: flex;
        flex-direction: column;
        padding: 20px;
        margin-top: 10px;
        border: 1px solid gray;
    }
</style>