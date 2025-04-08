<script setup>
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

</script>
<!-- O vue é separdo em 3 partes  -->

<!-- Bind -> ligar os elementos -->

<template>
  <!-- template -> Mexe com a estrutura -->
  <h1>{{ dizOi() }}</h1>
  <img v-bind:src="endImagem" alt="Imagem tigre">
</template>

<style scoped>
/* Style -> Nossa estrutrura de desing */

</style>
