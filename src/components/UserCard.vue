<template>

  <div class="card">
    <h2>USuario en Card</h2>
      <img src="${usuarios.picture.large}" class="card-img-top" alt="User Image">
      <div class="card-body">
    <!-- <h5 class="card-title">${user.name.first} ${user.name.last}</h5> -->
          <h5 class="card-title">
            {{ chat }}
          </h5>
      </div>
      <button></button>


  </div>
  </template>
  
  <script>
  import axios from 'axios';
export default {
  name: 'App',
  props:"chat",
  data() {
    return {
      usuarios:[],
      userName:"hola soy una card",
     
     
    };
  },
  methods: {
    async getUsuarios() {
      try {
        const url = "https://randomuser.me/api?results=1";
        const { data } = await axios.get(url);
         this.usuarios = data.results;
        //const userName = `${this.usuarios.name.first} ${this.usuarios.name.last}`;
        //const userPhoto = this.usuarios.picture.large;

        console.log(this.usuarios[0].name.first);
        return this.usuarios;
      } catch (error) {
        console.log(error);
      }
    },
  },
  mounted() {
   this.getUsuarios();
  },
 component:{
 

 }
};
  </script>
<style scoped>
.card{
  width: 18rem;
  border: solid rgb(74, 10, 71);
  margin: 20px;
}

</style>