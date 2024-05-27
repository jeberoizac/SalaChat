<template>

  <div class="chat">
    <h2>Sala de Chat</h2>
    <form action="">
      <textarea name="chat" id="" cols="40" rows="20" v-model="comentario">
        
      </textarea>
      {{ props.chat1 }}
      {{ props.chat2 }}
      <button @click="handleClick"> Click HIjo</button>
      
    </form>
  </div>
</template>

<script>
export default {
  name: 'SalaChat',
  props: {
    msg: String,
    chat1: String,
    chat2: String
  },
  // emits:addChat,
  data() {
    return {
      nuevoChat: "",
      Chats: [],
      comentario:"...",
      
    }
  },
  methods: {
    handleClick() {
      // Emitimos un evento llamado 'button-click' cuando se hace clic en el botón
      alert("hola desde SalaCHat")
      this.$emit('button-click');
    },
    agregarChat() {
      const nuevoChat = this.nuevoChat;
      this.Chats.push(nuevoChat);
      
    },
  }
}
</script>
<style>
.chat{
display: inline-flex;
width: 450px0px;
height: 450px;
border: solid yellow;

}
</style>