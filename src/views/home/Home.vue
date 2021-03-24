<template>
  <div id="home">
    <nav-bar>
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banner="banner"></home-swiper>
    <recommend-view :recommends="recommends" />
    <feature-view/>
    <tab-control class="tab-control" :titles="['流行','新款','精选']"></tab-control>
    <ul>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
      <li>1</li>
    </ul>
  </div>
</template>

<script>
import HomeSwiper from "./childComp/HomeSwiper";
import RecommendView from "./childComp/RecommendView";
import FeatureView from "./childComp/FeatureView";

import NavBar from "components/common/navbar/NavBar";
import TabControl from 'components/content/tabControl/TabControl'

import { getHomeMultidata, getHomeGoods } from "network/home";

export default {
  name: "Home.vue",
  components: {
    NavBar,
    HomeSwiper,
    RecommendView,
    FeatureView,
    TabControl
  },
  data() {
    return {
      banner: [],
      recommends: [],
      goods: {
        'pop': { page: 0, list: [] },
        'news': {page: 0, list: [] },
        'sell': {page: 0, list: [] },
      }
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
      getHomeGoods().then((res) => {
        console.log(res)
      })
    }
  },
  created() {
    this.getHomeMultidata();
    this.getHomeGoods("pop");
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
