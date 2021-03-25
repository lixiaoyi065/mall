<template>
  <div class="tab-control">
    <div class="tab-control-item"
         v-for="(item, index) in titles"
         :class="{active: currentIndex == index}"
          @click="itemClick(index)">
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: "TabControl.vue",
    props:{
      titles: {
        type: Array,
        default(){
          return [];
        }
      }
    },
    data(){
      return {
        currentIndex: 0
      }
    },
    methods: {
      itemClick(index){
        this.currentIndex = index;
      }
    }
  }
</script>

<style scoped>
  .tab-control{
    display: flex;

    height: 40px;
    line-height: 40px;
    font-size: 15px;
    text-align: center;
    background: #fff;
  }
  .tab-control-item{
    flex: 1;
  }

  .tab-control-item span{
    padding: 5px;
    border-bottom: 3px solid transparent;
  }

  .active span{
    border-bottom-color: var(--color-tint);
    color: var(--color-high-text);
  }
</style>
