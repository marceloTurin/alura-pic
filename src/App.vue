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
        fotos: [
          {
            url: 'https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcTwV4kVzT5McBdGSgqlVeRzubrNH_mOrrkKseDOGFURq20HmsrelEfMU7It',
            titulo: 'Cachorro'
          },
          {
            url: 'https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcTwV4kVzT5McBdGSgqlVeRzubrNH_mOrrkKseDOGFURq20HmsrelEfMU7It',
            titulo: 'Cachorrao'
          }
        ]
    }
  }
}    
  
</script>

<style>
  
</style>
