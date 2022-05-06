<template>
  <div class="info">
    <div class='basic-info'>
      <img width="100px" height="100px" :src="imgUrl" alt="error" :title="color">
      <div class="money-cards">
        <money-card v-for="(item,index) in moneyTickets" :value="index" :key="item" :money="item" :imgUrl="cardIcons[index]">
        </money-card>
      </div>
    </div>
    <div class="operation-money">
      <div class="operation">
        <img width="30px" height="30px" src="@/assets/bankTrade.png" alt="error">
        <img width="30px" height="30px" src="@/assets/dice.png" alt="error" @click="emitDice()">
        <img width="30px" height="30px" src="@/assets/trade.png" alt="error">
      </div>
      <div class="total-money">
        <img width='25px' height="25px" src="@/assets/totalMoney.png" alt="error" title="总计">:
        <span style="width:150px">{{totalMoney}}</span>
      </div>
    </div>
    <div class="property">
      显示拥有的地产，对应过路费。。。
    </div>
  </div>
</template>

<script>
  import MoneyCard from './player/MoneyCard.vue';
  export default {
    name: "PlayerInfo",
    props: {
      playerId:{
        type:Number,
        required:true
      },
      imgUrl: {
        type: String,
        default () {
          return require('@/assets/pic1.jpg');
        }
      },
      color: {
        type: String,
        required:true
      },
    },
    components: {
      MoneyCard,
    },
    data() {
      return {
        moneyTickets: [2, 4, 2, 2, 0, 0],
        moneyValues: [5,10,50,100,500,1000],
        cardIcons: [require('@/assets/redMoney.svg'), require('@/assets/blueMoney.svg'),
          require('@/assets/yellowMoney.svg'), require('@/assets/greenMoney.svg'),
          require('@/assets/pinkMoney.svg'), require('@/assets/orangeMoney.svg'),
        ],
        totalMoney: 0
      }
    },
    methods: {
      emitDice() {
        this.$EventBus.$emit('rollDice')
      }
    },
    created(){
      this.totalMoney = 0;
      for(let i in this.moneyTickets){
        this.totalMoney += this.moneyTickets[i]*this.moneyValues[i];
      }
    }
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
  .operation-money {
    margin-left: 10px;
    margin-top: 10px;
    display: flex;
    justify-content: space-between;
  }

  .total-money {
    height: 30px;
    width: 207px;
    border-radius: 10px;
    display: flex;
    justify-content: space-around;
    align-items: center;
    margin-bottom: 5px;
    margin-right: 7px;
    background-color: white;
  }

  .operation {
    width:100px;
    display: flex;
    justify-content: space-between;
  }

  .property {
    margin-left: 10px;
    margin-right: 7px;
    background: white;
    height: calc((100% - 160px));
  }
</style>