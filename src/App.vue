<template>
  <BaseContainer>
    <ChatWindow>
      <ChatMessage/>
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
