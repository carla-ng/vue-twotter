<template>
  
  <div id="app">
    <UserProfile />
  </div>

</template>

<script>
import UserProfile from './components/UserProfile'

export default {
  name: 'App',
  components: { UserProfile }
}
</script>

<style>
#app {
  background-color: #F3F5FA;
  color: #2c3e50;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100vh;

  display: flex;
  flex-direction: column;
}
</style>
