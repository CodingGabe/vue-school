<template>
  <HelloWorld />
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HellowWorld',
  components: {
    HelloWorld
  }
}
</script>

<style>
html {
  background-color: rgb(226 232 240);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  max-width: 54rem;
  margin: 3.75rem auto;
  padding: 2.5rem 4rem;
  background-color: #fff;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
}
@media (max-width: 576px) {
  #app {
    padding: 1rem;
  }
}

</style>
