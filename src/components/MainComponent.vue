<template>
    <div class="container-fluid">
        <div v-if="disks.length > 0" class="row justify-content-center align-items-center flex-wrap gap-3 col-8 offset-2">
            <FilterComponent :gArray="disks" @search="filterByGenre"/>
            <CardComponent 
            :key="index" 
            v-for="(disk,index) in disks" 
            :author=  disk.author 
            :poster= disk.poster 
            :title= disk.title 
            :year= disk.year  />
        </div>
        <div v-else>
            loading
        </div>
    </div>
</template>

<script>
import CardComponent from '@/components/CardComponent.vue';
import FilterComponent from '@/components/FilterComponent.vue'
import axios from 'axios';

export default {
    name:'MainComponent',
    components:{
        FilterComponent,
        CardComponent,
    },
    data(){
        return{
            disks: [],
            selectValue: ''
            
        }
    },

    props:{
        api: String, 
    },
    mounted(){
        this.loadData();
    },
    
    computed:{},
    methods:{
        loadData(){
            axios.get(this.api).then(
                response=>{                
                    if(response.status === 200){
                        console.log('response',response.data.response);
                        this.disks = response.data.response;
                    }
                }
            ).catch(error=>console.error('err',error))
        }, 
        filterByGenre(searchValue){
            console.log('sono qui', searchValue)
        }        
    }
}
</script>

<style lang="scss" scoped>
    @import '../style/variables';

    .container-fluid{
        background-color: $bg-main-color;
        height: 90vh;

        & > div{   
            padding: 40px 0;
        }
    }

</style>