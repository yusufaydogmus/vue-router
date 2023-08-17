<template>
<div class="container p-3">
  <h3 class="text-center"> Bookmark List</h3>
  <div class="row">
    <div class="col-6  offset-3">
    <router-view></router-view>

<MyCard/>
  </div>
  </div>
</div>

</template>
<script>
import MyCard from './components/MyCard.vue';
export default{
  components:{
    MyCard
  },
}
</script>