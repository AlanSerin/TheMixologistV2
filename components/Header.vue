<template>
  <div class="pt-1 d-flex justify-content-between mb-0 mb-md-4">
    <b-navbar toggleable="lg" type="dark" position="sticky" variant="outline" class="w-100 nav-class">

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-brand class="d-none d-lg-block" href="/TheMixologistV2/">The Mixologist V2</b-navbar-brand>
        <b-navbar-nav>
          <b-nav-item @click="getRandomDrink" href="#">Surprise Me</b-nav-item>
          <b-nav-item href="https://github.com/AlanSerin/TheMixologistV2">Github Link</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
      <!-- Right aligned nav items -->
<!--      <b-navbar-nav class="ml-auto">-->
<!--        <b-form-input v-model="search" @keydown.enter="searchDrinkHeader" size="sm" class="mr-sm-2 search-input" placeholder="Search"></b-form-input>-->
<!--      </b-navbar-nav>-->
    </b-navbar>
    <b-form-input v-if="$route.name === 'drink'" v-model="search" @keydown.enter="searchDrinkHeader" size="sm" class="search-input w-25" placeholder="Search"></b-form-input>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      search: null,
    }
  },
  methods: {
    async searchDrinkHeader() {
      const res = await this.$axios.$get('https://www.thecocktaildb.com/api/json/v1/1/search.php?s=' + this.search)
      await localStorage.setItem('searchResults', JSON.stringify(res.drinks))
      await console.log(res)
      if(this.$route.name == 'searchResult') {
        await this.$router.go(0)
      } else{
        await this.$router.push('/searchResult')
      }
    },
    getRandomDrink() {
      this.$axios.$get('https://www.thecocktaildb.com/api/json/v1/1/random.php').then(res => {
        console.log(res)
        localStorage.setItem('selectedDrink', JSON.stringify(res.drinks[0]))
        if(this.$route.name == 'drink') {
          this.$router.go(0)
        } else{
          this.$router.push('drink')
        }
      })
    },
  }
}
</script>

<style scoped>
@media only screen and (max-width: 700px) {
  .search-input {
    width: 75% !important;
  }
  .nav-class {
    padding-left: 1rem !important;
  }
  .search-input {
    margin-right: 1rem !important;
  }
}
.search-input {
  background-color: transparent;
  color: white;
  border-radius: 12px;
  margin: 0.75rem 2rem 0;
  max-width: 200px;
}
.nav-class {
  padding-left: 2rem;
}
.search-button {
  border-radius: 6px;
  background: #ffb700;
  border-color: #ffb700;
}
.search-button:hover {
  background: #ffb700;
  border-color: #ffb700;
}

::-webkit-input-placeholder { /* WebKit, Blink, Edge */
  color:    white;
}
:-moz-placeholder { /* Mozilla Firefox 4 to 18 */
  color:    white;
  opacity:  1;
}
::-moz-placeholder { /* Mozilla Firefox 19+ */
  color:    white;
  opacity:  1;
}
:-ms-input-placeholder { /* Internet Explorer 10-11 */
  color:    white;
}
::-ms-input-placeholder { /* Microsoft Edge */
  color:    white;
}

::placeholder { /* Most modern browsers support this now. */
  color:    white;
}
</style>
