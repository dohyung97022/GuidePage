<template>
  <MarkMap style="width: 100vw; height: 100vh"/>
</template>

<script>
import MarkMap from "@/components/MarkMap.vue";

export default {
  name: 'App',
  components: {
    MarkMap
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
</style>
