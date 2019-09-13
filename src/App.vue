<template>
  <div>
    <h1>{{titulo}}</h1>

    <ul>
      <li v-for="foto of fotos"> 
          <img :src="foto.url" :alt="foto.url">
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
  
</style>
