<template>
  <div id="app">
    <TransformadorTexto />
  </div>
</template>

<script>
import TransformadorTexto from './components/TransformadorTexto.vue';

export default {
  name: 'App',
  components: {
    TransformadorTexto
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
