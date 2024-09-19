<script>
import axios from 'axios';
export default{
    data(){
        return{
            archetypesList: [],
            selectedArchetype: '',
        }
    },
    methods:{
     getArchetypes() {
       axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
        .then((response) => {
          this.archetypesList = response.data;
    }) 
    },
    },
     created() {
       this.getArchetypes();
     },
}
</script>
<template>
    <select class="form-select mb-4" v-model="selectedArchetype" @change="onArchetypeChange">
      <option value="">Tutti gli Archetypes</option>
      <option v-for="archetype in archetypesList" :key="archetype.archetype_name" :value="archetype.archetype_name">
        {{ archetype.archetype_name }}
      </option>
    </select>
  </template>

<style lang="scss"  scoped>
@use 'bootstrap/scss/bootstrap.scss' as *;
select.form-select{
    background-color: white;
}

</style>