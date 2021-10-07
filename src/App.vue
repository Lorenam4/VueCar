<template>
  <div >
    <header-eco/>
    <home/>
    <footer-eco/>

  </div>
</template>

<script>

import HeaderEco from './components/HeaderEco.vue';
import Home from './views/Home.vue';
import FooterEco from './components/FooterEco.vue';
export default {
  name: 'App',
  components: {

    
    HeaderEco,
    Home,
    FooterEco

  }
};
</script>

<style lang="scss">
* {
  margin:0;
  padding: 0;
  box-sizing: border-box;
}
</style>
