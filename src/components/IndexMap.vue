<template>
  <div class="hello">
    <div class="player">
      <player-info :imgUrl="icons[0]"></player-info>
      <player-info :imgUrl="icons[1]"></player-info>
    </div>
    <div class="main-map">
      <main-map></main-map>
    </div>
    <div class="player">
      <player-info :imgUrl="icons[2]"></player-info>
      <player-info :imgUrl="icons[3]"></player-info>
    </div>
  </div>
</template>

<script>
  import MainMap from './MainMap.vue'
  import PlayerInfo from './PlayerInfo.vue'
  export default {
    name: 'IndexMap',
    components:{
      MainMap,
      PlayerInfo
    },
    props: {
    },
    data(){
      return {
        icons:[require('@/assets/pic1.jpg'),require('@/assets/pic2.jpg'),require('@/assets/pic3.jpg'),require('@/assets/pic4.jpg'),]
      }
    }
  }
</script>

<style scoped>
  .hello{
    display: flex;
    height: 100%;
    width: 100%;
  }
  .player {
    width:26%;
    background-color: lightblue;
  }
  .main-map {
    height: 100%;
    width: 48%;
    left: 100%;
    background: rgb(210, 210, 210);
  }
</style>