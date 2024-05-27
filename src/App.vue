<template>
  <h3>Usuarios</h3>

  <div class="container">
    <div class="row justify-content-center">
      <!-- <img :src="usuario.picture.large"/>
        <h3 class="card">{{ usuario.name.first }}</h3> -->
        <div class="col-md-3 justify-content-start align-items-start">
        <div class="card" v-for="(usuario, i) in usuarios" :key="i">
          <div v-if="i == 1">
            <img :src="usuario.picture?.large" />
            <h2 class="card-title">{{ usuario.name?.first }}</h2>
          </div>
        </div>
        <div >
          <input type="color" name="color1" id="color1" v-model="colorTexto1 " >
        </div>
        <div>
          <textarea name="" id="" cols="33" rows="8" v-model="chat1" :style="{ background: colorTexto1}"></textarea>
        </div>
        <button type="submit">Enviar</button>
      </div>
      <!-- sala de chat-->
      <div class="col-md-6 d-flex justify-content-center align-items-center chat">
        {{ chat2 }} {{ chat1 }}
        <SalaChat :cha1="chat1" :chat2="chat2"> </SalaChat>
      </div>

      <!--Usuario Random 2-->
      <div class="col-md-3 justify-content-end align-items-start">
        <div class="card" v-for="(usuario, i) in usuarios" :key="i">
          <div v-if="i == 0">
            <img :src="usuario.picture?.large" />
            <h2 class="card-title">{{ usuario.name?.first }}</h2>
          </div>
        </div>
        <div >
          <input type="color" name="color2" id="color2" v-model="colorTexto2">
        </div>
        <div>
          <textarea name="" id="" cols="33" rows="8" 
          v-model="chat2" :style="{ background: colorTexto2}"></textarea>
        </div>
        <button @click="addChat">Enviar</button>
        <SalaChat nuevoChat="Haz clic aquí" @handleClick="addChat" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
// import UserCard from "./components/UserCard.vue";
import SalaChat from "./components/SalaChat.vue";

export default {
  name: "App",
  data() {
    return {
      usuarios: [],
      usuario: "",
      chat1:"",
      chat2:"",
      colorTexto2:"",
      colorTexto1:"",
      grupoChat:"",
      chats:[],
    };
  },
  methods: {
    async getUsuarios() {
      try {
        const url = "https://randomuser.me/api?results=2";
        const { data } = await axios.get(url);
        //console.log(data.results);
        this.usuarios = data.results;
        const nombre = this.usuarios[0].name.first;
        console.log(nombre);
        return this.usuarios;
      } catch (error) {
        console.log(error);
      }
    },
    addChat(){

      alert("chat2")
      console.log(this.chat2);
      console.log(this.chat1);
    }
  },
  created() {
    this.getUsuarios();
  },
  component: {
    // UserCard,
    SalaChat,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  border: solid white;
  .div {
    border: solid green;
  }
}
.container {
    max-width: 100%;
  }


</style>
