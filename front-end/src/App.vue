<template>
<div id="page-container">
  <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.11.2/css/all.css">
  <div id="app">
    <Header></Header>
    <body id="body">
      
    </body>
    <Footer></Footer>
  </div>
</div>
</template>

<script>

import Footer from './components/Footer'
import Header from './components/Header'

export default {
  name: 'App',
  components: {
    Footer,
    Header
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
.table{
    width: 100% !important;
}
body {
  display: flex;
  flex-direction: column;
}

</style>
