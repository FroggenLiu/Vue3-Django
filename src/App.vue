<template>
  <div id="wrapper">
    <nav class="navbar is-dark">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item"><strong>Porvision Sysem</strong></router-link>
      </div>
      <div class="navbar-menu">
        <div class="navbar-end">
          <template v-if="$store.state.isAuthenticated">
            <router-link to="/dashboard" >Dashboard</router-link>
          </template>
          <template v-else>
            <router-link to="/" class="navbar-item">Home</router-link>
            <div class="buttons">
              <router-link to="/signin" class="button is-primary">Sign in</router-link>
            </div>
          </template>
        </div>
      </div>
    </nav>
    <section class="section">
      <router-view />
    </section>
    <footer class="footer">
      <p class="has-text-centered">Copyright (c) 2024 </p>
    </footer>
  </div>
</template>

<script>
  import axios from 'axios'
  
  export default{
    name: 'App',
    beforeCreate(){
      this.$store.commit('initializeStore')
      const token = this.$store.state.token
      if (token) {
        axios.defaults.headers.common['Authorization'] = "Token " + token
      }else{
        axios.defaults.headers.common['Authorization'] = ""
      }
    }
  }
</script>

<style lang="scss">
@import '../node_modules/bulma';
</style>
