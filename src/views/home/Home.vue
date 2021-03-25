<template>
  <div id="home">
    <nav-bar>
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banner="banner"></home-swiper>
    <recommend-view :recommends="recommends" />
    <feature-view/>
    <tab-control class="tab-control" :titles="['流行','新款','精选']" ></tab-control>
    <goods-list :goods="goods[type].list"/>
  </div>
</template>

<script>
import HomeSwiper from "./childComp/HomeSwiper";
import RecommendView from "./childComp/RecommendView";
import FeatureView from "./childComp/FeatureView";

import NavBar from "components/common/navbar/NavBar";
import TabControl from 'components/content/tabControl/TabControl'
import GoodsList from 'components/content/goods/GoodsList'

import { getHomeMultidata, getHomeGoods } from "network/home";

export default {
  name: "Home.vue",
  components: {
    NavBar,
    HomeSwiper,
    RecommendView,
    FeatureView,
    TabControl,
    GoodsList
  },
  data() {
    return {
      banner: [],
      recommends: [],
      goods: {
        'pop': { page: 0, list: [] },
        'new': {page: 0, list: [] },
        'sell': {page: 0, list: [] },
      },
      type: 'pop'
    };
  },
  methods: {
    getHomeMultidata() {
      getHomeMultidata().then((res) => {
        this.banner = res.data.banner.list;
        this.recommends = res.data.recommend.list;
        console.log(res.data);
      });
    },
    getHomeGoods(type) {
      getHomeGoods(type, this.goods[type].page+1 ).then((res) => {
        this.goods[type].page += 1;
        this.goods[type].list.push(...res.data.list)
      })
    }
  },
  created() {
    this.getHomeMultidata();
    this.getHomeGoods("pop");
    this.getHomeGoods("new");
    this.getHomeGoods("sell");
  },
};
</script>

<style scoped>
  #home{
    padding-top: 44px;
  }

  #nav-bar{
    background: var(--color-tint);
    color: #fff;

    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 9;
  }

  .tab-control{
    position: sticky;
    top: 44px;
  }
</style>
