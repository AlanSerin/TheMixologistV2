<template>
  <b-input-group class="search-input-group mx-auto">
    <template #prepend>
      <b-dropdown style="border-radius: 12px" variant="warning" size="md" id="dropdown-1" :text="searchType">
        <b-dropdown-item @click="searchType = 'Ingredient'">Ingredient</b-dropdown-item>
        <b-dropdown-item @click="searchType = 'Cocktail'">Cocktail</b-dropdown-item>
        <b-dropdown-item @click="searchType = 'Non-alcoholic'">Non-alcoholic</b-dropdown-item>
      </b-dropdown>
    </template>

    <b-form-input class="search-input" v-model="search" @keydown.enter="searchDrink" size="md"></b-form-input>
  </b-input-group>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      search: '',
      searchType: 'Cocktail'
    }
  },
  methods: {
    searchDrink() {
      if(this.searchType === 'Cocktail') {
        this.$axios.$get('https://www.thecocktaildb.com/api/json/v1/1/search.php?s=' + this.search).then(res => {
          localStorage.setItem('searchResults', JSON.stringify(res.drinks))
          console.log(res)
          if(this.$router.name !== 'searchResult') {
            this.$router.push('/searchResult')
            this.$emit('refreshPage')
          } else {
            this.$emit('refreshPage')
          }
        })
      }
      if(this.searchType === 'Ingredient') {
        this.$axios.$get('https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=' + this.search).then(res => {
          localStorage.setItem('searchResults', JSON.stringify(res.drinks))
          console.log(res)
          if(this.$router.name !== 'searchResult') {
            this.$router.push('/searchResult')
            this.$emit('refreshPage')
          } else {
            this.$emit('refreshPage')
          }
        })
      }
    },
  }
}
</script>

<style scoped>
@media only screen and (max-width: 750px) {
  .search-title {
    font-size: 3rem !important;
  }
  .search-text {
    font-size: 1.125rem !important;
    width: 100% !important;
    margin-bottom: 2.5rem !important;
  }
  .search-input-group {
    width: 100% !important;
  }
}
.search-input-group {
  width: 600px;
}
.search-input {
  background: white;
  /*border: 1px solid white;*/
}
</style>
