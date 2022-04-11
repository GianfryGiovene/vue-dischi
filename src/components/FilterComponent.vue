<template>
  <select @change="getOption($event)" name="" id="">
      <option value="all">All</option>
      <option :key="index" v-for="(disk,index) in gArray" :value="disk.genre">{{ disk.genre }}</option>
  </select>
</template>

<script>
export default {
    name:"FilterComponent",

    data(){
        return{
        optionValue:'all'
        }
    },
    props:{
        gArray :[]
    },

    methods:{
        getOption(e){
            this.optionValue = e.target.value;
            this.$emit('search', this.optionValue);
        }
    }

}
</script>

<style lang="scss" scoped>

</style>