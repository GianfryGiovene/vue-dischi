<template>
  <div id="app" class="h-100">
    <HeaderComponent logo="LOGO" />
    <MainComponent api="https://flynn.boolean.careers/exercises/api/array/music" />
  </div>
</template>

<script>
import HeaderComponent from '@/components/HeaderComponent.vue';
import MainComponent from '@/components/MainComponent.vue';


export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent,
  }
}
</script>

<style lang="scss">
@import './style/general';
@import './style/variables';

#app {
  height: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;  
}
</style>
