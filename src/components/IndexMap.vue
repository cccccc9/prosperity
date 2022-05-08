<template>
  <div class="hello">
    <land-trade></land-trade>
    <div class="player">
      <player-info :playerId="0" :imgUrl="icons[0]"></player-info>
      <player-info :playerId="3" :imgUrl="icons[1]"></player-info>
    </div>
    <div class="main-map">
      <main-map></main-map>
    </div>
    <div class="player">
      <player-info :playerId="1" :imgUrl="icons[2]"></player-info>
      <player-info :playerId="2" :imgUrl="icons[3]"></player-info>
    </div>
  </div>
</template>

<script>
  import MainMap from './MainMap.vue'
  import PlayerInfo from './PlayerInfo.vue'
  import LandTrade from './windows/LandTrade.vue'
  export default {
    name: 'IndexMap',
    components: {
      MainMap,
      PlayerInfo,
      LandTrade
    },
    props: {},
    data() {
      return {
        icons: [require('@/assets/pic1.jpg'), require('@/assets/pic2.jpg'), require('@/assets/pic3.jpg'), require(
          '@/assets/pic4.jpg'), ]
      }
    }
  }
</script>

<style scoped>
  .hello {
    display: flex;
    height: 100%;
    width: 100%;
  }

  .player {
    width: 26%;
    background-color: lightblue;
  }

  .main-map {
    height: 100%;
    width: 48%;
    left: 100%;
    background: rgb(141, 221, 227);
  }
</style>