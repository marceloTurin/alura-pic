

<template>
  <div>
    <h1 class="centralizado">{{titulo}}</h1>
    <input type="serach" class="filtro" @input="filtro = $event.target.value"  placeholder="filtre por parte do titulo">
    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="foto of fotosComFiltro">
        <meu-painel :titulo="foto.titulo">
          <imagem-responsiva :url="foto.url" :titulo="foto.titulo"></imagem-responsiva>
        </meu-painel> 
          
      </li>
    </ul>
  </div> 
</template>

<script>
 
  import Painel from '../shared/painel/Painel.vue';
  import ImagemResponsiva from '../shared/imagem-responsiva/ImagemResponsiva.vue';


  export default {

    components:{
      'meu-painel': Painel,
      'imagem-responsiva': ImagemResponsiva
    },

    data(){
      return {
        titulo: 'Alurapic',
        fotos: [],
        filtro:''
          
    }
  },
  computed:{
    fotosComFiltro(){
      if (this.filtro) {
        let exp = new RegExp(this.filtro.trim(),'i'); // expressão regular que filtra independe do maiusculo ou minusculo
        return this.fotos.filter(foto => exp.test(foto.titulo));
      } else{
        return this.fotos;
      }
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
  .centralziado {
    text-align: text;
  }

  .lista-fotos{
    list-style: none;
  }
  .lista-fotos .lista-fotos-item{
    display: inline-block;
  }

 
  .filtro{
    display: block;
    width: 100%;
  }
</style>
