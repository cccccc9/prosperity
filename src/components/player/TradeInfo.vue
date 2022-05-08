<template>
  <div class="trade-info" :class="{'selected-info':selectedId==playerId}">
    <div v-show="!display" class="shadow">
      <img width="99%" height="99%" :src="icons[playerId]" alt="error">
    </div>
    <div class="trade-fees">
      <span>请输入你的竞标价格：</span>
      <input :id="playerId" type="text" size="5">
      <!-- 如果id相同，取数据就会有问题 -->
    </div>
    <div class="operations">
      <img @click="getPrice" width="30px" height="30px" src="@/assets/submit.png" alt="error">
      <img @click="quit" width="30px" height="30px" src="@/assets/giveUp.png" alt="error">
    </div>
  </div>
</template>

<script>
  export default {
    name: "TradeInfo",
    props: {
      playerId: {
        type: String,
        required: true
      }
    },
    data() {
      return {
        display: true,
        maxPrice: 0,
        selectedId: 0,
        price: 0,
        icons: [require('@/assets/pic1.jpg'), require('@/assets/pic3.jpg'), require('@/assets/pic2.jpg'), require(
          '@/assets/pic4.jpg')]
      }
    },
    methods: {
      getPrice() {
        if (this.selectedId != Number(this.playerId)) return;
        this.price = document.getElementById(this.playerId).value;
        if (this.price % 5 != 0) {
          alert("请输入可以被钱币兑换的金额")
          return;
        }
        if (this.price > this.maxPrice) {
          this.maxPrice = this.price
          this.$EventBus.$emit('priceChange', this.maxPrice, this.playerId);
        } else {
          this.quit();
        }
      },
      quit() {
        console.log(this.selectedId != Number(this.playerId));
        if (this.selectedId != Number(this.playerId)) return;
        this.display = false;
        this.$EventBus.$emit('priceChange', 0, this.playerId);
      }
    },
    created() {
      this.$EventBus.$on('trade', (id, price) => {
        this.selectedId = id;
        this.maxPrice = Math.max(price, this.maxPrice);
      })
    }
  }
</script>

<style scoped>
  .trade-info {
    width: calc(50% - 2px);
    height: calc(50% - 2px);
    border: 1px solid rgb(255, 255, 255);
    background: rgb(168, 243, 159);
  }

  .selected-info {
    width: calc(50% - 4px);
    height: calc(50% - 4px);
    border: 2px solid rgb(0, 0, 0);
    background: rgb(168, 243, 159);
  }

  .shadow {
    z-index: 2000;
    width: 50%;
    height: 50%;
    position: fixed;
    opacity: 1;
  }

  .trade-fees {
    margin-top: 15px;
    margin-left: 5px;
    ;
  }

  .operations {
    margin-top: 15px;
    display: flex;
    justify-content: space-evenly;
  }
</style>