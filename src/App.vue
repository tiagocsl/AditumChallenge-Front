<template>
  <div id="app">
    <img class="imgLogo" alt="Aditum Logo" src="./assets/logo.png">
    <Home msg="Bem Vindo ao desafio da Aditum Pagamentos"/>    
  </div>
</template>

<script>
import Home from './views/Home'

export default {
  name: 'app',
  components:{
      Home
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #8d2773;
  margin-top: 60px;
  image-resolution: 50%;
}
.imgLogo{
  width: 20%;
  height: 20%;
}

.DataGrid {
    height: 500px;
    width: 500px;
}
revo-grid {
    height: 100%;
}
revogr-viewport-scroll .inner-content-table {
     height: 100%;
}

/* safari */
revogr-viewport-scroll .vertical-inner {
    display: flex;
    flex-direction: column;
}

revogr-viewport-scroll .content-wrapper {
    min-height: 100%;
    flex-grow: 1;
}

revogr-overlay-selection {
    display: block;
}
</style>



