<template>
  <div class="card">
    <img width='50px' height="30px" :src="imgUrl" alt="">
    <span style="width:50px">: {{money}}</span>
  </div>
</template>

<script>
  export default {
    name: "MoneyCard",
    props: {
      money: {
        type: Number,
        required: true,
        default () {
          return 0;
        }
      },
      index: {
        type:Number,
        default(){
          return 0;
        }
      },
      imgUrl:{
        type: String,
        default(){
          return require('@/assets/redMoney.svg')
        }
      }
    },
    data() {
      return {
        values:[5,10,50,100,500,1000]
      }
    },
    methods: {}
  }
</script>

<style scoped>
  .card {
    height: 30px;
    width: 100px;
    border-radius: 10px;
    display: flex;
    justify-content: space-around;
    align-items: center;
    margin-bottom: 5px;
    margin-left: 7px;
    background-color: white;
  }
</style>