<template>
  <div class="tab-bar-item" @click="ItemClick">
    <div v-if="!isactive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
    <div :style="activeStyle"><slot name="item-text"></slot></div>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props:{
    path:String,
    activeColor:{
      type:String,
      default:'red'
    }
  },
  data(){
    return{
    }
  },
  computed:{
    isactive(){
      return this.$route.path.indexOf(this.path)!==-1;
    },
    activeStyle(){
      return this.isactive ? {color:this.activeColor}:{}
    }
  },
  methods:{
    ItemClick(){
      this.$router.replace(this.path);
    }
  }
}
</script>

<style scoped>
.tab-bar-item{
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
}
.tab-bar-item img{
  height: 24px;
  width: 24px;
  margin-top: 3px;
  vertical-align: middle;
  margin-bottom: 2px;
}

</style>
