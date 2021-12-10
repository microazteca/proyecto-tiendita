<template>
  <div id="app">
    <Header />
    <UpArrow />
    <Services />
    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import UpArrow from "./components/atoms/UpArrow.vue";
import Services from "./components/Services.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    UpArrow,
    Services,
    Footer,
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
