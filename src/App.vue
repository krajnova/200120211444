<template>
  <div id="app">
    <ConsultantPage />
  </div>
</template>

<script>
import ConsultantPage from "./components/ConsultantPage.vue";

export default {
  name: "App",
  components: {
    ConsultantPage
  }
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

body,
h1,
h2,
h3,
p {
  margin: 0;
}

#app {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 14px;
  line-height: 20px;
  color: #333;
}
</style>
