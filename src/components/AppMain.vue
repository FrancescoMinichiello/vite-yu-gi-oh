<script>
import CardList from './CardList.vue';
import MainSearchArchetype from './MainSearchArchetype.vue';
export default{

  components:{
CardList,
MainSearchArchetype
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
        <div class="col py-4 d-flex gap-3 justify-content-center flex-wrap">
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