<template>
  <div class="dialog" v-if="display">
    <trade-info playerId="0"></trade-info>
    <trade-info playerId="1"></trade-info>
    <trade-info playerId="3"></trade-info>
    <trade-info playerId="2"></trade-info>
  </div>
</template>

<script>
  import TradeInfo from "../player/TradeInfo.vue"
  export default {
    name: "LandTrade",
    components: {
      TradeInfo
    },
    data() {
      return {
        display: false,
        maxPrice: Number.MIN_SAFE_INTEGER,
        selectedId: 0,
        ownerId: -1,
        players: [true, true, true, true]
      }
    },
    methods: {},
    created() {
      this.$EventBus.$emit('trade', this.selectedId, this.maxPrice);
      this.$EventBus.$on('landTrade',()=>{
        this.display = true;
      })
      this.$EventBus.$on('priceChange', (price, id) => {
        console.log('copy');
        if (price == 0) this.players[id] = false;
        this.maxPrice = Math.max(price, this.maxPrice);
        if (this.maxPrice == price && this.maxPrice != 0) {
          this.ownerId = id;
        }
        this.selectedId = ++this.selectedId % 4;
        let count = 0;
        while (!this.players[this.selectedId]&&count<4) {
          this.selectedId = ++this.selectedId % 4;
          count++;
        }
        count = 0;
        for (let i of this.players) {
          i && count++;
        }
        console.log(count,this.selectedId)
        if (count == 0) this.display = false;
        if (count == 1) this.$EventBus.$emit('trade', this.ownerId == -1 ? this.selectedId : this.ownerId, this
          .maxPrice);
        else this.$EventBus.$emit('trade', this.selectedId, this.maxPrice);
      })
    }
  }
</script>

<style scoped>
  .dialog {
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 500px;
    height: 500px;
    background: white;
    z-index: 1000;
    display: flex;
    flex-wrap: wrap;
  }
</style>