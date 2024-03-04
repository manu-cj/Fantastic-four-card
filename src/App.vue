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
* {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-image: repeating-linear-gradient(90deg, hsla(312,0%,73%,0.05) 0px,
  hsla(312,0%,73%,0.05) 1px,transparent 1px, transparent 104px),repeating-linear-gradient(0deg, hsla(312,0%,73%,0.05) 0px,
  hsla(312,0%,73%,0.05) 1px,transparent 1px, transparent 104px),repeating-linear-gradient(0deg, hsla(312,0%,73%,0.07) 0px,
  hsla(312,0%,73%,0.07) 1px,transparent 1px, transparent 26px),repeating-linear-gradient(90deg, hsla(312,0%,73%,0.07) 0px, 
  hsla(312,0%,73%,0.07) 1px,transparent 1px, transparent 26px),linear-gradient(135deg, hsl(235,44%,34%),hsl(235,44%,34%));
}

main {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  align-content: center;
  gap: 20px;
}
</style>
