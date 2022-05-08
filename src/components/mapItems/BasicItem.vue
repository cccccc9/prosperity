<template>
  <div class="item" :class="top==true?'item-top':'item-left'" :style="{'background-color':itemColor}">
    <div class="content" :class="top==true?'inner-top':'inner-left'" :title="ownners[ownner]">
      <!-- {{title}} -->
      <img v-if="landStatus==0" :title="title" width="30px" height="30px" :src="imgUrl" alt="error">
      <img v-if="landStatus==1" :title="title" width="30px" height="30px" :src="landStyle" alt="error">
      <div v-for="item in location" :key="item.title" :title="item.title">
        <img width="30px" height="30px" v-if="item.sectionId==sectionId" :src="item.color" alt="error">
      </div>
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
          return '#9A80B0';
        }
      },
      title: {
        type: String,
        default () {
          return '';
        }
      },
      imgUrl: {
        type: String,
        default () {
          return require('@/assets/road.png');
        }
      },
      sectionId: {
        type: Number,
        default () {
          return 0;
        }
      },
      location: {
        type: Array,
        required: true
      },
      // TODO 位置描述
      description: {
        type: String,
        default () {
          return ''
        }
      }
    },
    data() {
      return {
        landStatus: 0, // 描述土地状态
        ownner: 4, // 土地拥有者
        ownners:["小丸子","懒羊羊","海绵宝宝","小新",""],
        price: 0, // 土地价格
        fees: 0, //过路费
        landStyle: null,
      }
    },
    methods: {},
    created(){
       this.$EventBus.$on("buyLand", (url,id) => {
        if(id==this.sectionId){
          this.landStatus = 1;
          this.landStyle = url;
        }
      })
    }
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
    border: 1px white solid;
  }

  .item-left {
    height: 45px;
    width: 92px;
    border: 1px white solid;
  }

  .content {
    /* background-color: white; */
    font-size: 16px;
    display: flex;
    justify-content: center;
    align-items: center;
    user-select: none;
    overflow: hidden;
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