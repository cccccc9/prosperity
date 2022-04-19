<template>
  <div class="item" :class="top==true?'item-top':'item-left'" :style="{'background-color':itemColor}">
    <div class="content" :class="top==true?'inner-top':'inner-left'">
      {{title}}
    </div>
  </div>
</template>

<script>
  export default {
    name: "BasicItem",
    props: {
      top: {
        type: Boolean,
        default () {
          return true;
        }
      },
      itemColor: {
        type: String,
        default () {
          return 'green';
        }
      },
      title:{
        type: String,
        default(){
          return '';
        }
      },
      // TODO 位置描述
      description:{
        type:String,
        default(){
          return ''
        }
      }
    },
    data() {
      return {
        landStatus:'',// 描述土地状态
        ownner:'', // 土地拥有者
        price:0, // 土地价格
        fees:0, //过路费
      }
    },
    methods: {}
  }
</script>

<style scoped>
  .item {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .item-top {
    height: 92px;
    width: 45px;
    border: 1px black solid;
  }

  .item-left {
    height: 45px;
    width: 92px;
    border: 1px black solid;
  }

  .content {
    background-color: white;
    font-size: 16px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .inner-top {
    height: 92px;
    width: 31px;
    writing-mode: vertical-lr;
  }

  .inner-left {
    height: 31px;
    width: 92px;
  }
</style>