<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
export default{

  components:{
    AppHeader,
    AppMain
  },
    data(){
        return{

        }
    }
}
</script>

<template>
   <AppHeader/>
   <AppMain/>
</template>

<style lang="scss"  scoped>
@use 'bootstrap/scss/bootstrap.scss' as *;
</style>