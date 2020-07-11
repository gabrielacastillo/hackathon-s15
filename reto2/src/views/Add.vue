<template>
  <div class="page__agregar">
    <div class="agregar">
      <h4 class="title">Agregar Video</h4>
      <hr>
      <div class="inputs">
          <input type="text" placeholder="Titulo" v-model="video.titulo">
          <input type="text" placeholder="url-video" v-model="video.imagen">
      </div>
      <textarea cols="30" rows="10" placeholder="descripcion" v-model="video.descripcion">
      </textarea>
      <div class="buttons">
          <button @click="addVideo()">Agregar</button>
          <router-link to="/" tag="button">Cancelar</router-link>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: 'Add',
  components: {
    // HelloWorld,
  },
  data: () => ({
    video: {},
  }),
  methods: {
    addVideo() {
      fetch('http://localhost:3000/videos', {
        method: 'POST',
        body: JSON.stringify(this.video),
        headers: { 'Content-Type': 'application/json' },
      })
        .then((res) => {
          console.log(res);
          return res.json();
        })
        .then((data) => {
          console.log(data);
          this.$router.go(-1);
        });
    },
  },
};
</script>

<style scoped lang="scss">
.page__agregar{
    width: 500px;
    margin: 0 auto;
}

.page__agregar .inputs{
    display: flex;
    height: 40px;
    margin-top: 20px;
}

.inputs input{
    flex-grow: 1;
}

.inputs input:first-child{
    margin-right: 20px;
}

.page__agregar textarea{
    margin-top: 20px;
    width: 100%;
}

.page__agregar .buttons{
    width: 300px;
    margin: 20px auto 0 auto;
    display: flex;
    height: 40px;
}

.page__agregar .buttons button{
    flex-grow: 1;
    cursor: pointer;
}

.page__agregar .buttons button:first-child{
    margin-right: 20px;
    background-color: #FF5252;
    color: white;
}
</style>
