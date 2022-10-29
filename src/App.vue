<template>

  <div id="app">
    <nav>
      <img src="./assets/github-nav.png" alt="logo github" width="60" height="60"/>
      <p id="title">Buscador de Perfil</p>
    </nav>

    <div id="form">
      <input type="text" placeholder="Insira o nome do Perfil" id="profile" v-model="profileField" />
      <button type="button" id="button_s" @click="getProfile">
        <img src="./assets/lupa3.png" width="30" height="30">
      </button>
    </div>
    <div>
      <div v-if="displayCard">
        <CardVue :infoProfile="dataProfileJSON"/>
      </div>
    </div>
  </div>

</template>

<script>
import CardVue from './components/Card.vue';
import Axios from 'axios'
import swal from 'sweetalert'

export default {
  name: 'App',
  data(){
    return{
      profileField : "",
      dataProfileJSON: {},
      displayCard: false
    }
  },
  methods: {
    async getProfile(){
      let urlBase = "https://api.github.com/users/"
      
      await Axios.get(urlBase + this.profileField)
        .then(res =>{
          this.dataProfileJSON = res.data
          this.displayCard = true
        })
        .catch(err => {
          swal("Erro ao buscar usuário","Usuário não existe ou falha na requisição","error")
          console.error(err)
        })
    }
  },
  components: {
    CardVue
  }
  }
</script>

<style src="./styles/Home.css"></style>
