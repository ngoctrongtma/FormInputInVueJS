<template>
  <FormInput/>
</template>

<script>
import FormInput from './components/FormInput.vue';

export default {
  name: 'App',
  components: {
    FormInput,
  },
};
</script>

<style>
body {
  background: rgba(238, 238, 238, 0.596);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
