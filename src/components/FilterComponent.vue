<template>
  <select @change="getOption($event)" name="">
      <option value="">All</option>
      <option :key="index" v-for="(genre,index) in gArray" :value="genre">{{ genre }}</option>
  </select>
</template>

<script>
export default {
    name:"FilterComponent",

    data(){
        return{
            genreValue:'all',   
        }
    },
    props:{
        gArray: Array,
    },

    methods:{
        
        getOption(e){
            this.genreValue = e.target.value;
            this.$emit('search', this.genreValue);
        },
        
    }

}
</script>

<style lang="scss" scoped>

</style>