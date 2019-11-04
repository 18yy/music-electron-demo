<template>
  <div id="wrapper">
    <div class="main">
      <div class="list" v-for="item in playlists" :key="item.id">
        <img :src="item.coverImgUrl" alt="">
        <p>{{item.name}}</p>
      </div>
    </div>
    <playBar></playBar>
  </div>
</template>

<script>
  import playBar from './playBar/bar'

  export default {
    name: 'landing-page',
    components: { playBar},
    data(){
      return {
        playlists: []
      }
    },
    created(){
       this.$axios({
          method:'get',
          url:'http://localhost:3000/top/playlist?limit=9&order=hot'
        }).then((response) =>{        
          console.log(response.data.playlists);
          this.playlists = response.data.playlists;      
        }).catch((error)=>{
          console.log(error)
        })
      }
  }
</script>

<style scoped>
  #wrapper {
    height: 100vh;
    width: 100vw;
  }
  .main{
    padding: 48px 96px 80px 96px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
  .list {
    width: 260px;
    height: 200px;
    border: 1px solid #ccc;
    margin-bottom: 48px;
  }
  /* .list:nth-child(3n+0) {
    width: 265px;
    height: 200px;
    border: 1px solid #ccc;
    margin-right: 0;
    margin-bottom: 48px;
  } */
  .list img{
    width: 100%;
    height: 70%;
    background: rgb(66,109,171)
  }
</style>
