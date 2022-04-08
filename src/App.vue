<template>
  <div id="app" class="container-fluid">
    <HeaderComponent id="header" class=""/>
    <MainComponent id="main"/>
    
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import MainComponent from './components/MainComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent,
  }
}
</script>

<style lang="scss">
  @import 'bootstrap/scss/bootstrap';
  @import '@/style/variables';


#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  #header{
    background-color: $bg-header-color;
    
  }
  #main{}
}
</style>
