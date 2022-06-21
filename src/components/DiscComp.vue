<template>
    <div class="container bgColor py-5  mt-3">
        <div class="row row-cols-5 text-white bg-card mx-3">
            <!-- Card si genereano in base al v-for basato sull'array filteredDisc generato al return dell'if (vedi "computed") -->
            <CardComp v-for="(element, index) in filteredDisc" 
                    :key="index"
                    :image="element.poster"
                    :titolo="element.title"
                    :nome="element.author"
                    :anno="element.year"
                />        
    </div>    
    </div>
  
</template>

<script>
    //importo axios
    import axios from 'axios';
    import CardComp from './CardComp.vue';    

    export default {        
        name: 'DiscComp', 
        components: {
            CardComp
        },  
        props:{
            //definisco tipologia del props passato da App.vue
            passaGenSelProps: String
        },  
        computed:{
            //filtro per stabilire quali card visualizzare
            filteredDisc(){
                //se passaGenSelProps vuoto => mostra tutti i dischi
                if(this.passaGenSelProps === ''){
                    return this.dischi;  
                //altriemnti
                }else{
                    return this.dischi.filter((elem) => {
                        return elem.genre.includes(this.passaGenSelProps)
                    })
                }
            }            
        }, 
        data(){
            return{
                dischi:[],
                generi:[]
            }
        },  
        created(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
                    .then( (res) =>{    
                        console.log(res.data.response);                    
                        this.dischi = res.data.response; 
                        
                        this.dischi.forEach( (elem) => {
                            if(!this.generi.includes(elem.genre))
                            this.generi.push(elem.genre)
                        })

                        this.$emit('generiPronti', this.generi)
                    })                    
        }
    }
</script>

<style scoped lang="scss">
.bgColor{
    background-color:#2f3a46;    
}

</style>