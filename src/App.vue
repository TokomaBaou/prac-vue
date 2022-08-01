<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 in CodeSandbox!" />
</template>

// <script>
// import HelloWorldVue from "./components/HelloWorld.vue";
// export default {
//   name: "App",
//   components: {
//     HelloWorld: HelloWorldVue,
//   },
// };
//
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

<template>
  <div>
    <!-- 1 -->
    <v-alert
      class="message"
      v-for="val in messages"
      :key="val"
      border="top"
      :color="type === 'info' ? 'blue lighten-2' : 'red lighten-2'"
      dark
      dense
      dismissible
    >
      {{ val }}
    </v-alert>
  </div>
</template>

<script>
import messageStore from "../store/message-store"; //2
export default {
  name: "Message",
  watch: {
    //3
    $route() {
      messageStore.clearMessageInf();
    },
  },
  computed: {
    //4
    type() {
      return messageStore.state.type;
    },
    messages() {
      return messageStore.state.messages;
    },
  },
};
</script>

<style scoped>
.message {
  position: relative;
  top: 50px;
}
</style>