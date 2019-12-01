<template>
  <!-- <img src="../../assets/img/tabbar/me.png">
  <div class="tab-bar-item">首页</div> -->
  <div class="tab-bar-item"  @click="itemClick">
      <slot v-if="!isActive" name="item-icon"></slot>
      <slot v-else name="item-icon-active"></slot>
      <div :class="{active: isActive}">
        <slot name="item-text"></slot>
      </div>
      
  </div>
</template>

<script>
export default {
    name: 'TabBarItem',
    props: {
      path: String,
      activeColor: {
        type: String,
        default: "red"
      }
    },
    data() {
      return {
        
      }
    },
    methods: {
      itemClick() {
        this.$router.replace(this.path);
      }
    },
    computed: {
      isActive() {
         return this.$route.path.indexOf(this.path) != -1;
      },
      // activeStyle() {
      //   return this.isActive ? {color: activeColor} : {}
      // }
     
    }
}
</script>

<style>
.tab-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
}
.tab-bar-item img {
  height: 24px;
  width: 24px;
  margin-top: 3px;
  vertical-align: 0px;
}
.active {
  color:palevioletred;
}
</style>