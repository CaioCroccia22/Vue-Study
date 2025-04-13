<script setup>
import { reactive } from "vue";


// O script -> Onde vai ter o código (lógica funcional)
// A gente desenvolve elementos html com base nos nossos imports
const nome = 'Caio Croccia Pereira de Carvalho'
const meuObj = {
  nome: 'Caio Croccia',
  filmeFavorito: 'Creed'
}

function dizOi(){
  return `${nome} diz oi`;
}

const endImagem = "https://static.vecteezy.com/ti/fotos-gratis/t2/36324708-ai-gerado-cenario-do-uma-tigre-caminhando-dentro-a-floresta-foto.jpg"

const gostaDeTigre = false

const imagemLeao = 'https://images.unsplash.com/photo-1585468274952-66591eb14165?fm=jpg&q=60&w=3000&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OHx8bGUlQzMlQTNvfGVufDB8fDB8fHww'
const gostaDeLeao = true

// let contador = 0
const estado = reactive({
  contador: 0,
  email: '',
  Saldo: 5000,
  Transferindo: 0,
  nomes: [],
  nomeAInserir: '',
})

function incrementar() {
  estado.contador++;
}

function decrementar() {
  estado.contador--;
}

function alteraEmail(evento){
  estado.email = evento.target.value
}

function mostrarSaldoFuturo(){
  // Desestruturação de objetos, ao inves de colocar o estado.saldo, coloca o {{{saldo}}} = estado 
  const { Saldo, Transferindo} = estado
  return Saldo - Transferindo
}

function validaValor(){
  const { Saldo, Transferindo} = estado
  return Saldo > Transferindo
}



function cadastrarNome(){
  if(estado.nomeAInserir.length >= 3){
    estado.nomes.push(estado.nomeAInserir);
  }else{
    alert('Digite mais caracteres')
  }  
}

</script>
<!-- O vue é separdo em 3 partes  -->

<!-- Bind -> ligar os elementos -->

<template>
  <!-- template -> Mexe com a estrutura -->
  <h1>{{ dizOi() }}</h1>
  <!-- <img v-bind:src="endImagem" alt="Imagem tigre"> -->
  <img v-if="gostaDeTigre" v-bind:src="endImagem" alt="">
  <img v-else-if="gostaDeLeao"  :src="imagemLeao" alt="">
  <h2 v-else>Não curte animais</h2>
  <!-- <img v-show="gostaDeTigre" src="endImagem" alt=""> -->
  <!-- <img :src="imagemLeao" alt=""> -->

  <br />
  <hr />
{{ estado.contador }}
<button @click="incrementar" type="button">+</button>
<button @click="decrementar" type="button">-</button>

<br />
<hr />

{{ estado.email }}
<input type= "email" @keyup="alteraEmail">

<br />
<hr />
  Saldo: {{ estado.Saldo }} <br>
  Transferindo: {{ estado.Transferindo }} <br>
  Saldo depois da transferência: {{ mostrarSaldoFuturo() }}<br>
  <input :class="{ invalido: !validaValor() }" @keyup="evento => estado.Transferindo = evento.target.value" type="number" placeholder="Quantia para transferir">


<br>
<hr />
<input type="text" @keyup="evento => estado.nomeAInserir = evento.target.value">
<button type="button" @click="cadastrarNome">Cadastrar Nome</button>
<ul>
  <li v-for="nome in estado.nomes">{{ nome }}</li>
</ul>

<h3 v-for="nome in estado.nomes">{{ nome }}</h3>
</template>

<style scoped>
/* Style -> Nossa estrutrura de desing */
img{
  width: 200px;
}

.invalido{
  outline-color: red;
  border-color: red;
}
</style>
