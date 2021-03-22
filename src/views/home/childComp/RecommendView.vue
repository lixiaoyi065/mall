<template>
  <div class="recommend">
    <div class="recommend-item" v-for="item in recommends" :key="item.id">
      <a :href="item.link">
        <img :src="item.image" alt="" />
        <div>{{ item.title }}</div>
      </a>
    </div>
  </div>
</template>
<script>
export default {
  name: "RecommendView",
  props: {
    recommends: {
      type: Array,
      default() {
        return {};
      },
    },
  },
};
</script>
<style scoped>
.recommend {
  width: 100%;
  display: flex;
  padding: 10px 0 20px;
  border-bottom: 15px solid #eee;
  overflow: hidden;
}
.recommend-item {
  flex: 1;
  text-align: center;
  font-size: 12px;
  overflow: hidden;
}
.recommend-item img {
  width: 85px;
  height: 85px;
  margin-bottom: 10px;
}
</style>
