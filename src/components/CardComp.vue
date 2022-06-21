<template>  
    <div class="col text-center">
        <img :src="image" class="img-fluid my-3" alt="">    
        <h3 class="my-3">
            {{titolo}}
        </h3>
        <h4 class="my-3 text-white-50">
            {{nome}}
        </h4>
        <h4 class="my-3 text-white-50">
            {{anno}}
        </h4>
    </div>
</template>

<script>
    
    export default {
    name: 'CardComp',
    //specifico tipologia props
    props: {
        image:String,
        titolo:String,
        nome:String,
        anno:String,
    }
    }
</script>

<style scoped lang="scss">
</style>