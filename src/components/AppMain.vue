<script>
import CardList from './CardList.vue';
export default{

  components:{
CardList
  },
    data(){
        return{
       
        }
    }
}
</script>

<template>
   <main>
    <div class="container-fluid box-cards py-4 px-5">
      <div class="row">
        <div class="col">
        <CardList/>
        </div>
      </div>
    </div>
   </main>
</template>

<style lang="scss"  scoped>
@use 'bootstrap/scss/bootstrap.scss' as *;
.box-cards{
  background-color: #C18236;
}
.col{
  background-color: white;
}

</style>