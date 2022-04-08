<template>
  <div class="diskcard col-2 row ">
      <img :src="poster" :alt="title" class="w-100">
      <h5 class="">{{ title }}</h5>
      <span>{{ author }}</span>
      <span>{{ year }}</span>
  </div>
</template>

<script>
export default {
name:'CardComponent',
props:{
    author: String,
    poster: String,
    title: String,
    year: String,
}
}
</script>

<style lang="scss" scoped>
    @import '../style/variables';

    .diskcard{
        background-color: $bg-card-color;
        height: 300px;
        color: #fff;
        margin: 5px;
        padding: 10px;
    }
</style>