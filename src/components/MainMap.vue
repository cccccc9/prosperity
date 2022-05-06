<template>
  <div class="map">
    <div>
      <div class="game-map">
        <div :sectionId="27" class="corner1">
          <div class="corner-flags">
            <div v-for="item in locations" :key="item">
              <img width="30px" height="30px" v-if="item.sectionId==27" :src="item.color" alt="error">
            </div>
          </div>
        </div>
        <div class="map-top">
          <basic-item :sectionId="28" :location="locations" :title="`光谷大道`"></basic-item>
          <basic-item :sectionId="29" :location="locations" :title="`私人住宅`" :itemColor="`#433F67`"
            :imgUrl="require('@/assets/house.png')"></basic-item>
          <basic-item :sectionId="30" :location="locations" :title="`关山路`"></basic-item>
          <basic-item :sectionId="31" :location="locations" :title="`地铁`" :itemColor="`#FFB031`"
            :imgUrl="require('@/assets/subway.png')"></basic-item>
          <basic-item :sectionId="32" :location="locations" :title="`鲁磨路`"></basic-item>
          <basic-item :sectionId="33" :location="locations" :title="`豪华酒店`" :itemColor="`#ECB9B3`"
            :imgUrl="require('@/assets/hotel.png')"></basic-item>
          <basic-item :sectionId="34" :location="locations" :title="`珞喻路`"></basic-item>
          <basic-item :sectionId="35" :location="locations" :title="`珞雄路`"></basic-item>
        </div>
        <div :sectionId="0" class="corner2" title="起点+董事会（可领工资）">
          <div class="corner-flags">
            <div v-for="item in locations" :key="item">
              <img width="30px" height="30px" v-if="item.sectionId==0" :src="item.color" alt="error">
            </div>
          </div>
        </div>
        <div class="map-mid">
          <basic-item :sectionId="26" :location="locations" :top='false' :title="`中南路`"></basic-item>
          <basic-item :sectionId="25" :location="locations" :top='false' :itemColor="`#FFFD91`"></basic-item>
          <basic-item :sectionId="24" :location="locations" :top='false' :title="`首义路`"></basic-item>
          <basic-item :sectionId="23" :location="locations" :top='false' :title="`税务局`" :itemColor="`#9BACD8`"
            :imgUrl="require('@/assets/tax.png')">
          </basic-item>
          <!-- 支付改善税 -->
          <basic-item :sectionId="22" :location="locations" :top='false' :title="`江汉路`"></basic-item>
          <basic-item :sectionId="21" :location="locations" :top='false' :title="`高速公路`" :itemColor="`#FFB031`"
            :imgUrl="require('@/assets/highway.png')">
          </basic-item>
          <basic-item :sectionId="20" :location="locations" :top='false' :title="`汉街`"></basic-item>
          <basic-item :sectionId="19" :location="locations" :top='false' :title="`樱花大道`"></basic-item>
        </div>
        <div class="map-content">
          <div v-show="isDicing" class="dice">
            <span class="number">{{diceNums1}}</span>
            <span class="number">{{diceNums2}}</span>
          </div>
        </div>
        <div class="map-mid">
          <basic-item :sectionId="1" :location="locations" :top='false' :title="`监狱`" :itemColor="`#B1B1B1`"
            :imgUrl="require('@/assets/prison.png')">
          </basic-item>
          <basic-item :sectionId="2" :location="locations" :top='false' :title="`光谷一路`"></basic-item>
          <basic-item :sectionId="3" :location="locations" :top='false' :title="`光谷二路`"></basic-item>
          <basic-item :sectionId="4" :location="locations" :top='false' :title="`光谷三路`"></basic-item>
          <basic-item :sectionId="5" :location="locations" :top='false' :title="`光谷四路`"></basic-item>
          <basic-item :sectionId="6" :location="locations" :top='false' :title="`税务局`" :itemColor="`#9BACD8`"
            :imgUrl="require('@/assets/tax.png')">
          </basic-item>
          <!-- 个人财产税 -->
          <basic-item :sectionId="7" :location="locations" :top='false' :itemColor="`#FFFD91`"></basic-item>
          <basic-item :sectionId="8" :location="locations" :top='false' :title="`光谷四路`"></basic-item>
        </div>
        <div :sectionId="18" class="corner3">
          <div class="corner-flags">
            <div v-for="item in locations" :key="item">
              <img width="30px" height="30px" v-if="item.sectionId==18" :src="item.color" alt="error">
            </div>
          </div>
        </div>
        <div class="map-top">
          <basic-item :sectionId="17" :location="locations" :title="`未来三路`"></basic-item>
          <basic-item :sectionId="16" :location="locations" :itemColor="`#FFFD91`"></basic-item>
          <basic-item :sectionId="15" :location="locations" :title="`未来一路`"></basic-item>
          <basic-item :sectionId="14" :location="locations" :title="`税务局`" :itemColor="`#9BACD8`"
            :imgUrl="require('@/assets/tax.png')"></basic-item>
          <!-- 土地税 -->
          <basic-item :sectionId="13" :location="locations" :title="`光谷七路`"></basic-item>
          <basic-item :sectionId="12" :location="locations" :title="`跨江大桥`" :itemColor="`#FFB031`"
            :imgUrl="require('@/assets/bridge.png')"></basic-item>
          <basic-item :sectionId="11" :location="locations" :title="`光谷六路`"></basic-item>
          <basic-item :sectionId="10" :location="locations" :title="`光谷五路`"></basic-item>
        </div>
        <div :sectionId="9" class="corner4">
          <div class="corner-flags">
            <div v-for="item in locations" :key="item">
              <img width="30px" height="30px" v-if="item.sectionId==9" :src="item.color" alt="error">
            </div>
          </div>
        </div>
      </div>
      <div class="memory">For Elizabeth J. Magie Phillips</div>
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
      return {
        diceNums1: 1,
        diceNums2: 1,
        isDicing: false,
        locations: [{
          sectionId: 0,
          color: require("@/assets/redFlag.png")
        }, {
          sectionId: 0,
          color: require("@/assets/greenFlag.png")
        }, {
          sectionId: 0,
          color: require("@/assets/yellowFlag.png")
        }, {
          sectionId: 0,
          color: require("@/assets/blueFlag.png")
        }],
        selected: 0
      }
    },
    methods: {
      rollDice() {
        this.isDicing = true;
        this.diceNums1 = '?';
        this.diceNums2 = '?';
        setTimeout(() => {
          this.diceNums1 = Math.floor(Math.random() * 6) + 1;
          this.diceNums2 = Math.floor(Math.random() * 6) + 1;
          this.locations[this.selected].sectionId += this.diceNums1 + this.diceNums2;
          this.locations[this.selected].sectionId %= 36;
          this.selected++;
          this.selected %= 4;
        }, 500)
        setTimeout(() => {
          this.isDicing = false;
        }, 2000)
      },
    },
    created() {
      this.$EventBus.$on("rollDice", () => {
        this.rollDice();
      })
    }
  }
</script>

<style scoped>
  #area {
    width: 200px;
    height: 200px;
  }

  .map {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
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
    background: url("@/assets/map_content.jpg");
    background-size: 100%;
  }

  .dice {
    height: 100px;
    width: 100px;
    background: white;
    border: 3px solid black;
    border-radius: 25%;
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    opacity: 85%;
  }

  .number {
    font-size: 35px;
    user-select: none;
  }

  .corner1 {
    height: 94px;
    width: 94px;
    border-radius: 94px 0 0 0;
    background-color: #FBC2A6;
  }

  .corner2 {
    height: 94px;
    width: 94px;
    border-radius: 0 94px 0 0;
    background-color: #8AB6C9;
  }

  .corner-flags {
    margin-top: 20px;
    width: 60px;
    display: flex;
    flex-wrap: wrap;
  }

  .corner3 {
    height: 94px;
    width: 94px;
    border-radius: 0 0 0 94px;
    background-color: #FBC2A6;
    float: left;
  }

  .corner4 {
    height: 94px;
    width: 94px;
    border-radius: 0 0 94px 0;
    background-color: #FBC2A6;
    float: right;
  }
</style>