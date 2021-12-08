<template>
  <div id="app">
    <Header />
    <Services />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Services from "./components/Services.vue";

export default {
  name: "App",
  components: {
    Header,
    Services,
  },
};
</script>

<style src="@/assets/css/main.css"></style>
<style src="@/assets/css/reset.css"></style>

<style lang="scss" scoped>
#app {
  overflow-x: hidden;
}
</style>
