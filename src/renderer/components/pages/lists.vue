<template>
  <div class="main">
      <div class="list" v-for="item in playlists" :key="item.id">
        <img :src="item.coverImgUrl" alt="">
        <p>{{item.name}}</p>
      </div>
  </div>
</template>

<script>


  export default {
      name: 'lists-page',
      props: {
        playlists: {
        
        }
    }
  }
</script>

<style scoped>
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
    cursor: pointer;
  }
  .list img{
    width: 100%;
    height: 70%;
    background: rgb(66,109,171)
  }
</style>
