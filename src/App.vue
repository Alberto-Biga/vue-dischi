<template >
  <div >
    <!-- richiamo componente Header -->
    <HeaderComp
    :passaGeneriProps="generi"
    @inviaGenereSel="ottieniGenereSel"/>
    <!-- richiamo componente Disc (card album) -->
    <DiscComp
    @generiPronti="ottieniGeneri"
    :passaGenSelProps="genereSelezionato"/>
  </div>
</template>

<script>
//importo bootstrap
import "bootstrap"
//importo Header
import HeaderComp from './components/HeaderComp.vue'
//importo Disc
import DiscComp from './components/DiscComp.vue'

export default {
  name: 'App',
  components: {
    HeaderComp,
    DiscComp,    
  },
  data(){
    return {
      //array momentaneamente vuoto per i generi
      generi: [],
      //dato vuoto, da riempire tramite metodo "ottieniGenereSel"
      genereSelezionato:''
    }
  },
  methods:{
    ottieniGeneri(mieiGeneri){
      this.generi = mieiGeneri
    },
    ottieniGenereSel(genSel){
      this.genereSelezionato = genSel
    }
  }
}
</script>

<style  lang="scss">
@import "bootstrap/dist/css/bootstrap.min.css";
body{
  background-color: #1e2d3b;  
}
</style>
