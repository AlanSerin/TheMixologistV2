<template>
  <div>
    <b-container fluid>
      <b-row>
        <b-col class="search-container">
          <h1 class="text-light text-center mt-4 mb-3">Search</h1>
          <SearchBar @refreshPage="refreshPage" />
<!--          <p class="text-light text-center">All the drinks related to search are displayed here</p>-->
        </b-col>
      </b-row>
      <b-row v-if="results" :key="resultsKey">
        <b-col class="mt-4 mt-md-0" cols="12">
          <h2 class="text-light result-title" style="margin-bottom: 2.5rem">{{ results.length }} Search Results</h2>
        </b-col>
        <b-col @click="onCardClick(result.idDrink)" style="margin-bottom: 2.5rem;" v-for="(result, index) in results" :key="index">
          <div class="result-card mx-auto mx-sm-0">
            <img class="result-image mb-2" :src="result.strDrinkThumb" alt="">
            <div v-if="result.strAlcoholic" class="text-truncate" style=" color: #ffb700;">{{ result.strAlcoholic }} - {{ result.strCategory }}</div>
            <h4 class="mb-1">{{ result.strDrink }}</h4>
            <div class="instructions">{{ result.strInstructions ? result.strInstructions : 'Mint green with lots of fizz and an unidentifiable spice on the rim of the glass. The drink smells like pears and tastes like cave rock. Powdered unicorn horn is rumoured to be a key ingredient.' }}</div>
<!--            <b-row>-->
<!--              <b-col class="mb-2" v-for="(ingredient,index) in 15" :key="'ingredient-'+index" v-if="result['strIngredient'+index]">-->
<!--                <div class="ingredient">-->
<!--                  {{ result['strIngredient'+index] }}-->
<!--                </div>-->
<!--              </b-col>-->
<!--            </b-row>-->
          </div>
        </b-col>
      </b-row>
      <b-row v-else>
        <b-col class="text-center">
          <div class="error-number text-light">404</div>
          <h1 class="text-light error-text mb-4">No Results Found</h1>
<!--          <h5 class="text-light">The drink you searched for doesnt exist</h5>-->
          <b-button style="border-radius: 16px; width: 200px" variant="warning" class="text-light error-button" @click="$router.back()">Go Back</b-button>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  name: "searchResult",
  data() {
    return {
      results: null,
      resultsKey: 0,
    }
  },
  mounted() {
    if(JSON.parse(localStorage.getItem('searchResults')) === undefined) {
      this.$router.back()
    }
    this.results = JSON.parse(localStorage.getItem('searchResults'))
  },
  methods: {
    onCardClick(id) {
      this.$axios.$get('https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=' + id).then(res => {
        console.log(res)
        localStorage.setItem('selectedDrink', JSON.stringify(res.drinks[0]))
        this.$router.push('drink')
      })
    },
    refreshPage() {
      this.resultsKey = this.resultsKey + 1
      this.results = JSON.parse(localStorage.getItem('searchResults'))
    },
  }
}
</script>

<style>
@media only screen and (max-width: 556px) {
  .result-title {
    font-size: 2rem;
  }
  .result-card {
    max-width: 90vw !important;
  }
  .result-image {
    width: 90vw !important;
  }
  .instructions {
    max-width: 80vw !important;
  }
  .error-number {
    font-size: 5rem !important;
  }
  .error-text {
    font-size: 2rem;
  }
  .error-button {
    width: 80% !important;
  }
  .search-container {
   margin-bottom: 2rem !important;
  }
}
.search-container {
  margin-bottom: 4rem;
}
.instructions {
  display: -webkit-box;
  max-width: 200px;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
.error-number {
  font-size: 7rem;
}
.ingredient {
  background-color: #ffb700;
  padding: 4px 8px;
  border-radius: 6px;
  white-space: nowrap;
}
.result-card {
  color: white;
  cursor: pointer;
  max-width: 260px;
  transition: transform 0.2s;
}
.result-image {
  width: 250px;
  border-radius: 6px;
}
.result-card:hover {
  transform: scale(1.05);
}
.btn-md, .btn-group-md > .btn {
  border-radius: 20px;
}
.btn-warning, .btn-warning:hover, .btn-warning:active, .btn-warning:focus {
  color: white !important;
  background: #ffb700;
}
.form-control-md {
  border-radius: 20px;
}
</style>
