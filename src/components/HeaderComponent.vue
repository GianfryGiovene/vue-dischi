<template>
    <div class="container-fluid">
        
        <div class="row align-items-center">
            {{ logo }}
        </div>

    </div>
</template>

<script>


export default {
    name:'HeaderComponent',
    props:{
        logo: String,
    }

}
</script>

<style lang="scss" scoped>
    @import '../style/variables';
    

    div{
        color: #fff;
        background-color: $bg-header-color;
        height:10vh;
    }
</style>