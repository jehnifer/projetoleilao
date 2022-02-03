<template>
    <div>
    <header id="header">
      <router-link to="/home">Home</router-link> |
      <router-link to="/participantes">Participantes</router-link> |
      <router-link to="/leiloes">Leilões</router-link>
    </header>
    <router-view/>
    </div>
</template>

<script>
export default {

}
</script>

<style>

header {
  flex-shrink: 0;
    background: greenyellow;
    position: absolute;
    width: 100%;
    top: 0px;
}
</style>
