<template>
  <div id="app">
    <app-message></app-message>
    <h1>网页路由</h1>
    <hr>
    <!-- <a href="/">Home</a> -->
    <router-link to="/">Home</router-link>
    <router-link to="/users">Users</router-link>
    <router-link to="/users/10">Users 10</router-link>
    <router-link to="/users/12">Users 10</router-link>
    <hr>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      
    }
  }
}
</script>

<style lang="scss">
</style>
