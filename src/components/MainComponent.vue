<template>
    <div class="container-fluid">
        <div v-if="!isLoading" class="row justify-content-center align-items-center flex-wrap gap-3 col-8 offset-2">
            <FilterComponent :gArray="genreNoDuplicateArray" @search="filterByGenre"/>
            <CardComponent 
            :key="index" 
            v-for="(disk,index) in filteredGenre" 
            :author=  disk.author 
            :poster= disk.poster 
            :title= disk.title 
            :year= disk.year
            :genre= disk.genre
            :value= searchThisValue  />
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
            searchThisValue: '',
            genreArray: [],
            genreNoDuplicateArray: [],
            
        }
    },

    props:{
        api: String, 
    },
    mounted(){
        this.loadData();
        this.genreNoDuplicateArrayGenerator()
    },
    created: function(){
        
    },

    computed:{
        
        isLoading(){
            return this.disks.length === 0;
        },
        
        filteredGenre(){
            return this.disks.filter(item=> item.genre.toLowerCase().includes(this.searchThisValue.toLowerCase()))
        }
    },

    methods:{
        // acquisizione api
        loadData(){
            axios.get(this.api).then(
                response=>{                
                    if(response.status === 200){
                        console.log('response',response.data.response);
                        this.disks = response.data.response; 
                        this.genreNoDuplicateArrayGenerator()
                    }
                }
            ).catch(error=>console.error('err',error))
            
        }, 

        filterByGenre(searchValue){
            if(!searchValue !== 'all'){  
                this.searchThisValue = searchValue;
            }    
        },
        // funzione per creare array genere senza duplicati
        genreNoDuplicateArrayGenerator(){
            this.disks.forEach(element => {
                this.genreArray.push(element.genre) ;             
            });  
            this.genreNoDuplicateArray=[...new Set(this.genreArray)];
            console.log('patate',this.genreNoDuplicateArray);
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