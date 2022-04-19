<template>
  <div class="info">
    <div class='basic-info'>
      <img width="100px" height="100px" :src="imgUrl" alt="">
      <slot name="pic"></slot>
      <div class="money-cards">
        <money-card v-for="(item,index) in moneyCards" :key='item' :money="item" :imgUrl="cardIcons[index]">
        </money-card>
      </div>
    </div>
  </div>
</template>

<script>
  import MoneyCard from './player/MoneyCard.vue';
  export default {
    name: "PlayerInfo",
    props:{
      imgUrl:{
        type: String,
        default(){
          return require('@/assets/pic1.jpg');
        }
      }
    },
    components: {
      MoneyCard,
    },
    data() {
      return {
        moneyCards: [5, 10, 50, 100, 500, 1000],
        cardIcons:[require('@/assets/redMoney.svg'),require('@/assets/blueMoney.svg'),
        require('@/assets/yellowMoney.svg'),require('@/assets/greenMoney.svg'),
        require('@/assets/pinkMoney.svg'),require('@/assets/orangeMoney.svg'),]
      }
    },
    methods: {}
  }
</script>

<style scoped>
  .info {
    width: calc(100% - 2px);
    height: calc(50% - 2px);
    border: 1px solid black;
    background-color: rgb(188, 232, 253);
  }

  .basic-info {
    margin-top: 10px;
    margin-left: 10px;
    display: flex;
    height: 100px;
  }

  .money-cards {
    display: flex;
    flex-wrap: wrap;
    margin-bottom: -5px;
  }
</style>