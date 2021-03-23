<template>
  <div id="home">
    <nav-bar>
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banner="banner"></home-swiper>
    <recommend-view :recommends="recommends" />
    <feature-view/>
    <ul>
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
import NavBar from "components/common/navbar/NavBar";
import HomeSwiper from "./childComp/HomeSwiper";
import RecommendView from "./childComp/RecommendView";
import FeatureView from "./childComp/FeatureView";

import { getHomeMultidata } from "network/home";

export default {
  name: "Home.vue",
  components: {
    NavBar,
    HomeSwiper,
    RecommendView,
    FeatureView,
  },
  data() {
    return {
      banner: [],
      recommends: [],
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
  },
  created() {
    this.getHomeMultidata();
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


</style>
