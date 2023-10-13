<template>
  <div class="container">
    <NavComp/>

    <router-view></router-view>
  </div>
</template>

<script>
import NavComp from './components/NavComp.vue';

export default {
  name: 'App',
  components: {
    NavComp
  }
}
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
.container {
  display: flex;
  flex-direction: column;
  align-items: center;

}
</style>
