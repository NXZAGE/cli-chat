<template>
  <BaseContainer>
    <ChatWindow v-on:send-messsage="send">
      <ChatMessage v-for="message in messages" :key="message.id">
        <template #username> {{ message.author }} </template>
        <template #time> {{ message.datetime }} </template>
        <template #text> {{ message.text }} </template>
      </ChatMessage>
    </ChatWindow>
  </BaseContainer>
</template>

<script>
import BaseContainer from "./components/BaseContainer.vue";
import ChatMessage from "./components/ChatMessage.vue";
import ChatWindow from "./components/ChatWindow.vue";

export default {
  name: 'App',
  components: {
    BaseContainer,
    ChatMessage,
    ChatWindow
  },
  methods: {
    loadMessages() {
      this.axios.get("https://61bcd385d8542f0017824a2a.mockapi.io/messages")
        .then((responce) => {
          let messages = responce.data;
          messages.forEach(element => {
            let message = {
              author: element.author,
              datetime: element.datetime,
              text: element.text,
              id: element.id,
            };
            this.messages.push(message);
          });
        });
    },
    send(){
      console.log("send method");
    },
    sendMessage(){
      let message = {
        username: "aboba",
        text: "abbbbbbbbbbbbbbbbbbbbbbo",
      };
      console.log("sended????");
      this.axios({
        method: "post",
        url: "http://37.77.104.246/api/chat/sendmessage.php",
        data: {
          username: message.username,
          text: message.text,
        },
      }).then((responce) => {
        console.log(responce);
        this.loadMessages();
      });
    }
  },
  data() {
    return {
      messages: [],
    }
  },
  mounted() {
    this.loadMessages();
  }
}
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
</style>
