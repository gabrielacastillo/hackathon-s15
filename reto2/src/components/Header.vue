<template>
  <div class="header">
    <h3>VIDEO TV</h3>
    <router-link class="agregar" to="/add">Agregar Video</router-link>
  </div>
</template>

<script>
export default {
  name: 'Header',
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.header{
    height: 100px;
    background-color: #FF5252;
}

.header h3{
    color: white;
    display: inline-block;
    margin-top: 38px;
    text-shadow: 0px 2px 2px #000000;
}

.header .agregar{
    color: white;
    display: inline-block;
    position: absolute;
    right: 0;
    margin-top: 38px;
    text-shadow: 0px 2px 2px #000000;
    cursor: pointer;
    text-decoration: none;
}
</style>
