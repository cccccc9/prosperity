<template>
  <div class="map">
    <div>
      <div class="game-map">
        <div class="corner1"></div>
        <div class="map-top">
          <basic-item :title="`光谷大道`"></basic-item>
          <basic-item :title="`私人住宅`" :itemColor="`black`"></basic-item>
          <basic-item :title="`关山路`"></basic-item>
          <basic-item :title="`地铁`" :itemColor="`orange`"></basic-item>
          <basic-item :title="`鲁磨路`"></basic-item>
          <basic-item :title="`豪华酒店`" :itemColor="`pink`"></basic-item>
          <basic-item :title="`珞喻路`"></basic-item>
          <basic-item :title="`珞雄路`"></basic-item>
        </div>
        <div class="corner2"></div>
        <div class="map-mid">
          <basic-item :top='false' :title="`中南路`"></basic-item>
          <basic-item :top='false' :itemColor="`yellow`"></basic-item>
          <basic-item :top='false' :title="`首义路`"></basic-item>
          <basic-item :top='false' :title="`税务局`" :itemColor="`lightblue`"></basic-item>
          <!-- 支付改善税 -->
          <basic-item :top='false' :title="`江汉路`"></basic-item>
          <basic-item :top='false' :title="`高速公路`" :itemColor="`orange`"></basic-item>
          <basic-item :top='false' :title="`汉街`"></basic-item>
          <basic-item :top='false' :title="`樱花大道`"></basic-item>
        </div>
        <div class="map-content">
          <div class='main-content'>
            <div id='area'></div>
          </div>
        </div>
        <div class="map-mid">
          <basic-item :top='false' :itemColor="`lightgrey`" :title="`监狱`"></basic-item>
          <basic-item :top='false' :title="`光谷一路`"></basic-item>
          <basic-item :top='false' :title="`光谷二路`"></basic-item>
          <basic-item :top='false' :title="`光谷三路`"></basic-item>
          <basic-item :top='false' :title="`光谷四路`"></basic-item>
          <basic-item :top='false' :title="`税务局`" :itemColor="`lightblue`"></basic-item>
          <!-- 个人财产税 -->
          <basic-item :top='false' :itemColor="`yellow`"></basic-item>
          <basic-item :top='false' :title="`光谷四路`"></basic-item>
        </div>
        <div class="corner3"></div>
        <div class="map-top">
          <basic-item :title="`未来三路`"></basic-item>
          <basic-item :itemColor="`yellow`"></basic-item>
          <basic-item :title="`未来一路`"></basic-item>
          <basic-item :title="`税务局`" :itemColor="`lightblue`"></basic-item>
          <!-- 土地税 -->
          <basic-item :title="`光谷七路`"></basic-item>
          <basic-item :title="`跨江大桥`" :itemColor="`orange`"></basic-item>
          <basic-item :title="`光谷六路`"></basic-item>
          <basic-item :title="`光谷五路`"></basic-item>
        </div>
        <div class="corner4"></div>
      </div>
      <div class="memory">For Elizabeth Magie</div>
    </div>
  </div>
</template>

<script>
  import BasicItem from './mapItems/BasicItem.vue'	

  export default {
    name: "MainMap",
    components: {
      BasicItem
    },
    data() {
      return {}
    },
    methods: {
    },
    created() {
      var mydice = dice(document.getElementById('area'))
      mydice.roll(5)
    }
  }
</script>

<style scoped>
  #area {
    width:100%;
    height:100%;
  }
  .map {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    /* align-items: center; */
  }

  .game-map {
    margin-top: 2px;
    width: 564px;
    height: 564px;
    background-color: white;
    border-radius: 94px;
    display: grid;
    grid-template-columns: 94px 376px 94px;
    grid-template-rows: 94px 376px 94px;
  }

  .memory {
    font-size: 14px;
    text-align: center;
  }

  .map-top {
    display: flex;
  }

  .map-content {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgb(230, 230, 230);
  }

  .main-content {
    /* background: red; */
    border: 8px rgb(176, 0, 0) solid;
    /* border: 8px rgb(0, 123, 27) solid; */
    /* TODO 繁荣模式下显示为绿色 */
    width: 200px;
    height: 200px;
    position: relative;
    text-align: center;
  }

  .main-content:before {
    content: "";
    position: absolute;
    top: -8px;
    left: -8px;
    height: 200px;
    width: 200px;
    border: 8px rgb(176, 0, 0) solid;
    /* border: 8px rgb(0, 123, 27) solid; */
    -webkit-transform: rotate(135deg);
    -moz-transform: rotate(135deg);
    -ms-transform: rotate(135deg);
    -o-transform: rotate(135deg);
    transform: rotate(135deg);
  }

  .corner1 {
    height: 94px;
    width: 94px;
    border-radius: 94px 0 0 0;
    background-color: rgb(222, 0, 0);
  }

  .corner2 {
    height: 94px;
    width: 94px;
    border-radius: 0 94px 0 0;
    background-color: rgb(138, 204, 225);
  }

  .corner3 {
    height: 94px;
    width: 94px;
    border-radius: 0 0 0 94px;
    background-color: rgb(222, 0, 0);
    float: left;
  }

  .corner4 {
    height: 94px;
    width: 94px;
    border-radius: 0 0 94px 0;
    background-color: rgb(222, 0, 0);
    float: right;
  }
</style>