<template>
  <div class="body-holder mt-2 d-flex justify-content-xl-between justify-content-center">
    <b-container fluid>
      <b-row>
        <b-col class="d-block d-md-none">
          <b-carousel id='drinkcarousel' img-height="275px" controls :interval='3000'>
            <b-carousel-slide img-blank>
              <img class="drinks-slide" src="https://www.thecocktaildb.com/images/media/drink/5noda61589575158.jpg" alt="">
            </b-carousel-slide>
            <b-carousel-slide img-blank>
              <img class="drinks-slide" src="https://www.thecocktaildb.com/images/media/drink/stwiva1619704025.jpg" alt="">
            </b-carousel-slide>
            <b-carousel-slide img-blank>
              <img class="drinks-slide" src="https://www.thecocktaildb.com/images/media/drink/qgdu971561574065.jpg" alt="">
            </b-carousel-slide>
          </b-carousel>
        </b-col>
        <b-col xl="7" class="mt-2 mb-4 mb-xl-0 text-center text-md-left">
          <h1 class="page-title mb-lg-4 mb-m2">The whole world of mixology at your fingertips</h1>
          <div class="page-text w-75 mx-auto mx-md-0">Become a bartender one recipe at a time. Every alcoholic and non-alcoholic cocktail and drink known to humankind brought to you by The Mixologist(V2) and TheCocktailDB</div>
          <div class="d-flex justify-content-between justify-content-md-start">
            <b-button block @click="$router.push('/search')" class="start-button mr-3" size="lg">Get Started</b-button>
            <b-button block class="github-link mt-0" size="lg">Github Link</b-button>
          </div>
        </b-col>
        <b-col xl="5" class="position-relative w-75 d-xl-block d-none mt-2">
          <img class="drinks" style="position: absolute; top: 0; right: 0" src="https://www.thecocktaildb.com/images/media/drink/5noda61589575158.jpg" alt="">
          <img class="drinks" style="position: absolute; top: 20%; right: 20%;" src="https://www.thecocktaildb.com/images/media/drink/stwiva1619704025.jpg" alt="">
          <img class="drinks" style="position: absolute; right: 40%; top: 40%" src="https://www.thecocktaildb.com/images/media/drink/qgdu971561574065.jpg" alt="">
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
<style lang="css">
@media only screen and (max-width: 750px) {
  .page-title {
    font-size: 2rem !important;
  }
  .page-text {
    font-size: 1rem !important;
    width: 100% !important;
    margin-bottom: 2.5rem !important;
  }
  .start-button {
    width: 50% !important;
  }
  .github-link {
    width: 50% !important;
  }
}
.img-fluid {
  height: 260px;
}
.carousel-caption {
  padding: 0;
}
.drinks-slide {
  width: 225px;
  height: 225px;
  border-radius: 12px;
  box-shadow: 2px 2px 12px rgba(0, 0, 0, 0.73);
}
.drinks {
  width: 300px;
  border-radius: 12px;
  box-shadow: 2px 2px 16px black;
  transition: transform .2s;
}
.drinks:hover {
  z-index: 3;
  transform: scale(1.07);
}
.search-input-group {
  width: 95%;
  margin: auto;
}
.btn-lg, .btn-group-lg > .btn {
  border-radius: 20px;
}
.btn-warning, .btn-warning:hover, .btn-warning:active, .btn-warning:focus {
  color: white !important;
  background: #ffb700;
}
.form-control-lg {
  border-radius: 20px;
}
.search-input {
  background: white;
  /*border: 1px solid white;*/
}
.body-holder {
  color: white;
  flex: 1;
  overflow: auto;
}
.neonPink {
  background-color: #ffffff;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  box-shadow:
    0 0 7px #ff8cc0,
    0 0 14px #ff8cc0,
    0 0 20px #ff6ab7,
    0 0 40px #f551a8,
    0 0 60px #f551a8,
    0 0 80px #f09,
    0 0 100px #f09,
    0 0 120px #f09,
    0 0 140px #f09,
    0 0 160px #f09,
    0 0 192px #f09,
    0 0 202px #f09,
    0 0 225px #f09,
    0 0 235px #f09,
    0 0 251px #f09;
}
.neonBlue {
  position: absolute;
  bottom: 5%;
  right: 5%;
  background-color: #d0eafd;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  box-shadow:
    0 0 7px #73afff,
    0 0 14px #6eb3ff,
    0 0 20px #6cb5ff,
    0 0 40px #54a4f8,
    0 0 60px #3699ff,
    0 0 80px #0088ff,
    0 0 100px #0088ff,
    0 0 120px #0088ff,
    0 0 140px #0088ff,
    0 0 160px #0088ff,
    0 0 192px #0088ff,
    0 0 202px #0088ff,
    0 0 225px #0088ff,
    0 0 235px #0088ff,
    0 0 251px #0088ff;
}
.page-title {
  font-size: 5rem;
}
.page-text {
  font-size: 1.25rem;
  margin-bottom: 2.5rem;
}
.start-button {
  background: #ffb700;
  border-color: #ffb700;
  /*border-radius: 24px;*/

  width: 200px;
}
.start-button:hover {
  background: #ffb700;
  border-color: #ffb700;
}
.github-link {
  background: transparent;
  border-radius: 24px;
  width: 250px;
  border-color: white;
}
.github-link:hover {
  background: #0088ff;
  border-color: #0088ff;
}
</style>
