<template>
<div>
  <div class="form-show">
    <tab-item v-for="(list,index) in lists" :key="index" :title="list.title" :desc="list.desc" :link="list.link"></tab-item>
    <button @click="deleteAll" class="delete-all-btn" v-if="ButtonDel"> Delete All</button>

  </div>
</div>
</template>
<script>
import TabItem from './TabItem.vue';
export default {
  components: { TabItem },
  inject:['deleteAll'],
  name: "TabShow",
  data(){
    return{
      ButtonDel: false,
    }
  },
    props: {
    lists: {
      type: Array,
      default: () => [],
    },
  },
  watch:{ 
    lists(){
      if(this.lists.length > 0){
        this.ButtonDel = true;
      }else{
        this.ButtonDel = false;
      }
    }
  }
};
</script>
<style scoped>
.delete-all-btn{
  outline: none;
  border: none;
  padding: 15px 20px;
  background-color: #c9252c;
  color: #fff;
  display: block;
  cursor: pointer;
  font-size: 18px;
  border-radius: 10px;
  transition: 0.3s;
  margin: auto;
}
</style>
