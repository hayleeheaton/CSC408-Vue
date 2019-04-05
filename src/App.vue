<template>
  <div id="app">
      <header id = "header">Yellow Bucket</header>
    <div id="nav">
      <!--<router-link to="/">Home</router-link> |-->
      <!--<router-link to="/about">About</router-link> |-->
      <router-link to="/">Movies</router-link> |
      <router-link to="/customers">Customers</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
/* Add Google Font */
@import url('https://fonts.googleapis.com/css?family=Open+Sans:300,400,700');

/* This is where we inport our custom CSS files */
@import './assets/styles/custom.css';

#app {
  font-family: 'Avantgarde', TeX Gyre Adventor, URW Gothic L, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #d9eee9;
  color: #2c3e50;
}
#nav {
  text-align: right;
  font-size: 30px;
  background-color: #67917b;
  padding: 25px;
  a {

    color: #2c3e50;
    &.router-link-exact-active {
      color: #e2a300;
    }
  }
}
</style>
