<template>
  <div class="animated bounceInRight">
    <h3 class="title">为您推荐</h3>
    <div class="recommend">
      <ul class="recommend-content">
        <li class="item " v-for="(item,index) of forYouList" :key="index">
          <img class="pic" v-lazy="'./../../../static/image/'+item.hotImg" alt="">
          <router-link to="/detail">
            <div class="panel" @click="findCity(item)">
              <i class="el-icon-star-on love" @click="giveStar" :style="{'color':bgc}"></i>
              <span class="des">{{item.wantCount}}人想去这里</span>
            </div>
          </router-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Recommend",
    data(){
      return {
        bgc:'white'
      }
    },
    props:{
      forYouList: Array
    },
    methods:{
      findCity(item) {
        let cityHot = 'forYouList';
        this.$store.commit('changeCity',[item.cityName,cityHot]);
      },
      giveStar(e){
        e.preventDefault();
        // this.bgc = 'red';
      }
    }
  }
</script>

<style scoped>
  .recommend {
    width: 100%;
    min-height: 684px;
    position: relative;
  }

  .recommend-content {
    width: 86%;
    position: absolute;
    top: 0;
    left: 50%;
    transform: translate(-50%);
  }

  .item {
    width: 276px;
    height: 160px;
    float: left;
    margin-left: 11px;
    position: relative;
    margin-bottom: 11px;
  }

  .pic {
    width: 276px;
    height: 160px;
  }

  .panel {
    width: 276px;
    height: 160px;
    background-color: rgba(255, 255, 255, .3);
    position: absolute;
    top: 0;
    left: 0;
    display: none;
  }

  .love {
    position: absolute;
    left: 2px;
    bottom: 2px;
    z-index: 2;
    color: #fff;
    font-size: 15px;
  }

  .des {
    position: absolute;
    right: 2px;
    bottom: 2px;
    z-index: 2;
    color: #fff;
    font-size: 15px;
  }

  .item:hover .panel {
    display: block;
  }
</style>
