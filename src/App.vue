

<template>
  <div class="corpo">
    <h1 class="centralizado">{{titulo}}</h1>

    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="foto of fotos">
        <meu-painel :titulo="foto.titulo">
          <img class="imagem-responsiva" :src="foto.titulo" :alt="foto.titulo">
        </meu-painel> 
          
      </li>
    </ul>
  </div> 
</template>

<script>
  export default {
    data(){
      return {
        titulo: 'Alurapic',
        fotos: []
          
    }
  },
  created(){
    this.$http.get('http://localhost:3000/v1/fotos') // método get retorna uma promise
      .then(res => res.json()) // retorna a resposta do servidor e  converte em json
      .then(fotos =>  this.fotos = fotos, err => console.log(err)); //e coloca as informações no nosso array
  }
}    
  
</script>

<style>
  .corpo {
    font-family: Helvetica,sans-serif;
    width: 96%;
    margin: 0 auto;
  }

  .centralziado {
    text-align: text;
  }

  .lista-fotos{
    list-style: none;
  }
  .lista-fotos .lista-fotos-item{
    display: inline-block;
  }

  .imagem-responsiva{
    width: 100%
  }
</style>
