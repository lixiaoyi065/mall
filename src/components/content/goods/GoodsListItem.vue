<template>
  <div class="goods-item">
    <img :src="goodsItem.show.img">
    <div class="goods-info">
      <div class="title">{{goodsItem.title}}</div>
      <span class="price">￥ {{goodsItem.price}}</span>
      <span class="collection">{{goodsItem.cfav}}人已购买</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: "GoodsListItem.vue",
    props:{
      goodsItem: {
        type: Object,
        default(){
          return {}
        }
      }
    }
  }
</script>

<style scoped>
  .goods-item{
    margin: 10px 0;
    /* 防止多列布局，分页媒体和多区域上下文中的意外中断 */
    break-inside: avoid;

    background: #fff;
    -webkit-box-shadow: 0 0 10px rgba(0,0,0,.2);
    -moz-box-shadow: 0 0 10px rgba(0,0,0,.2);
    box-shadow: 0 0 10px rgba(0,0,0,.2);
    -webkit-border-radius: 6px;
    -moz-border-radius: 6px;
    border-radius: 6px;
    overflow: hidden;
  }

  .goods-item img{
    width: 100%;
    height: auto;
  }
  .goods-item .goods-info{
    padding: 8px;
    font-size: 14px;
  }

  .goods-item .goods-info .title{
    margin-bottom: 8px;
    font-size: 15px;
    word-break: keep-all;
    white-space: nowrap;
    -ms-text-overflow: ellipsis;
    text-overflow: ellipsis;
    overflow: hidden;
  }
  .goods-item .goods-info .price{
    font-size: 15px;
    color: var(--color-high-text);
    padding-right: 5px;
  }

  .goods-item .goods-info .collection{
    color: #909090;
  }
</style>
