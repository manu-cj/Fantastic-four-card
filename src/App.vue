<template>
  <main>
    <headerPage/>
    <cardProfile/>
  </main>

</template>

<script>
import cardProfile from './components/cardProfile.vue';
import headerPage from './components/headerPage.vue';

export default {
  name: 'App',
  components: {
   cardProfile,
   headerPage,
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
  background-color: #676768;
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
