<template>
  <div class="goods-list">
    <goods-list-item v-for="item in goods" :goods-item="item"></goods-list-item>
  </div>
</template>

<script>
  import GoodsListItem from './GoodsListItem'

  export default {
    name: "GoodsList.vue",
    props: {
      goods: {
        type: Array,
        default(){
          return []
        }
      }
    },
    components:{
      GoodsListItem
    }
  }
</script>

<style scoped>
  .goods-list{
    padding: 10px;
    column-count: 2;
    column-gap: 10px;
  }
</style>
