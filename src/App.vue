<template>
  <TopHeader />
  <HelloWorld />
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'
import TopHeader from '@/components/TopHeader.vue'

export default {
  name: 'HellowWorld',
  components: {
    HelloWorld,
    TopHeader
  }
}
</script>

<style>
html {
  background-color: rgb(226 232 240);
  margin: 0;
  box-sizing: border-box;
  -webkit-text-size-adjust: 100%;
  /* Prevent adjustments of font size after orientation changes in iOS */
  word-break: normal;
  -moz-tab-size: 4; tab-size: 4;
}
*, ::before, ::after {
  background-repeat: no-repeat; /* Set `background-repeat: no-repeat` to all elements and pseudo elements */
  box-sizing: inherit;
}
::before, ::after { text-decoration: inherit; /* Inherit text-decoration and vertical align to ::before and ::after pseudo elements */
  vertical-align: inherit;
}
* {
  padding: 0; /* Reset `padding` and `margin` of all elements */
  margin: 0;
}
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-color: #fff;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
  height: calc(100vh - 1rem);
}
@media (min-width: 576px) {
  #app {
    padding: 1rem;
  }
}

</style>
