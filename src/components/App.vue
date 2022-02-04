<template>
  <div class="app">
    <Header @onInputChange="onChangeHandler" />
    <Main :inputValue="inputValue" />
    <Footer />
  </div>
</template>

<script>
import Main from "./Main.vue";
import Header from "./Header.vue";
import Footer from "./Footer.vue";

export default {
  name: "App",
  components: {
    Main,
    Header,
    Footer,
  },
  methods: {
    onChangeHandler(value) {
      this.inputValue = value;
    },
  },
  data() {
    return {
      inputValue: "",
    };
  },
};
</script>

<style>
body {
  margin: 0;
  font-family: "Merriweather", sans-serif;
}

.app {
  background-color: #f6f3f3;
  height: 100vh;
  width: 100%;
  display: flex;
  flex-direction: column;
}
</style>
