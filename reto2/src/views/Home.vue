<template>
  <div class="body">
    <div class="home">
      <p class="title">Lista de videos</p>
      <div class="container">
        <div class="item" v-for="v in videos" :key="v.id">
          <div class="item__header">
            <img v-bind:src="v.imagen" alt />
          </div>
          <div class="item__content">
            <h5>{{v.titulo}}</h5>
            <span>{{v.visualizaciones}} visualizaciones</span>
            <p>{{v.descripcion}}</p>
            <button>Ver Detalle</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data: () => ({
    videos: [],
  }),
  components: {
    // HelloWorld,
  },
  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      fetch('http://localhost:3000/videos')
        .then((res) => {
          console.log(res);
          return res.json();
        })
        .then((data) => {
          console.log(data);
          this.videos = data;
        });
    },
  },
};
</script>

<style scoped lang="scss">
.body{
  padding: 20px;
  .title{
    height: 40px;
    vertical-align: middle;
    font-size: 20px;
    font-weight: bold;
  }
}

.container{
    display: grid;
    grid-template-columns: repeat(4, 1fr);
}

.item{
  margin-right: 20px;
  .item__header{
    height: 200px;
    text-align: center;
  }
  .item__header img{
    height: 100%;
  }
  .item__content h5{
    margin-top: 10px;
  }
  .item__content span{
    display: inline-block;
    margin-top: 10px;
  }
  .item__content p{
    margin-top: 10px;
  }
  .item__content button{
    margin-top: 10px;
    width: 100%;
    background-color: #00C1AA;
    color: white;
    height: 35px;
  }
}
</style>
