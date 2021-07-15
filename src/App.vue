<template>
  <div id="app" :style="{ backgroundImage: `url(${BG})` }">
    <CreateUser /> 
  </div>
</template>

<script>
import BG from "@/assets/img/bg.png";
import CreateUser from "./components/CreateUser.vue";
export default {
  name: "App",
  components: {
    CreateUser,
  },
  data() {
    return {
      BG
    };
  },
};
</script>

<style lang="sass">
*
  box-sizing: border-box
  margin: 0
  padding: 0

#app
  font-size: 16px
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50
  background-image: url("https://i.pinimg.com/736x/1f/32/de/1f32de75ae0a1ac218a902f6f361a6d7.jpg")
</style>
