<script>
import axios from 'axios'

export default {
  data() {
    return {
      cardsList: [],
      apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0"
    }
  },
  methods: {
    getCards(){
      axios.get(this.apiUrl)
      .then((response)=>{
        console.log(response.data.data);
        this.cardsList = response.data.data;
      })
    }
  },
  created() {
    this.getCards()
  },
}
</script>

<template>
  <div v-for="card in cardsList" :key="card.id">
    <p>{{ card.name }}</p>
  </div>
</template>

<style lang="scss"  scoped>
@use 'bootstrap/scss/bootstrap.scss' as *;
</style>