<template>
    <div class="container-fluid">
        <div class="row justify-content-center align-items-center flex-wrap gap-3 col-8 offset-2">
            <CardComponent 
            :key="index" 
            v-for="(disk,index) in disks" 
            :author=  disk.author 
            :poster= disk.poster 
            :title= disk.title 
            :year= disk.year  />
        </div>
    </div>
</template>

<script>
import CardComponent from '@/components/CardComponent.vue';
import axios from 'axios';

export default {
    name:'MainComponent',
    components:{
        CardComponent,
    },
    data(){
        return{
            disks: [],
        }
    },

    props:{
        api: String, 
    },
    mounted(){
        this.loadData();
    },
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
            
        }
    },


}
</script>

<style lang="scss" scoped>
    @import '../style/variables';

    .container-fluid{
        background-color: $bg-main-color;

        & > div{   
            padding: 40px 0;
        }
    }

</style>