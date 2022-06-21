<template>
  <div class="header d-flex justify-content-between align-items-center">    
      <img src="../assets/spotify-logo.png" alt=""> 
      <form action="">
        <label for="" class="form-label text-white">Seleziona un genere</label>
        <select 
          class="form-select"
          aria-label="Default select example"
          v-model="selected"
          @change="$emit('inviaGenereSel', selected)"
          >
          <option value="">Tutti i generi</option>
          <option v-for="(elem, index) in passaGeneriProps" :key="index" :value="elem">
            {{elem}}
          </option>
        </select>
      </form>   
  </div>
</template>

<script>
  export default {
    name: 'HeaderComp',
    props: {
      passaGeneriProps: Array
    },
    data(){
      return{
        selected: ''
      }
    }
  }
</script>

<style scoped lang="scss">
  .header{
    background-color: #2f3a46;
    height: 10vh;
    padding: 0 20px;

    img{
      height: 60%;
    }
  }
</style>
