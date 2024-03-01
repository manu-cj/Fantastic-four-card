<template>
  <main>
    <cardProfile/>
  </main>

</template>

<script>
import cardProfile from './components/cardProfile.vue';

export default {
  name: 'App',
  components: {
   cardProfile,
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

main {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  align-content: center;
}
</style>
