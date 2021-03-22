<template>
  <div>
    <nav-bar>
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banner="banner"></home-swiper>
    <recommend-view :recommends="recommends" />
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import HomeSwiper from "./childComp/HomeSwiper";
import RecommendView from "./childComp/RecommendView";

import { getHomeMultidata } from "network/home";

export default {
  name: "Home.vue",
  components: {
    NavBar,
    HomeSwiper,
    RecommendView,
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
</style>
