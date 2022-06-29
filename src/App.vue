<template>
  <div id="app">
    <TheHeader />
    <TheMain />
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TheMain from "./components/TheMain.vue";

export default {
  name: "App",
  components: {
    TheHeader,
    TheMain,
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');
* {margin: 0; padding: 0; box-sizing: border-box;}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  input::-webkit-input-placeholder {
        color: #fff;
}
}

#app,html{
  height: 100%;
  background-color: #141414;
  font-family: 'Bebas Neue', cursive;
}

</style>
