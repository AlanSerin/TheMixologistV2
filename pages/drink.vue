<template>
  <div v-if="drink" class="main-container">
    <b-container class="container-itself" fluid>
      <b-row class="position-relative row-row">
        <b-col class="left-side" order="2" order-xl="1" xl="6">
          <h1>{{ drink.strDrink }}</h1>
          <h3 style="color: #ffb700">{{ drink.strAlcoholic }} - {{ drink.strCategory }}</h3>
          <p class="mb-4">Mint green with lots of fizz and an unidentifiable spice on the rim of the glass. The drink smells like pears and tastes like cave rock. Powdered unicorn horn is rumoured to be a key ingredient.</p>
          <div class="mb-2">
            <h3>Ingredients</h3>
            <hr style="background-color: white; margin-top: 0">
            <div class="mb-2 mr-2 d-flex align-self-center" v-for="(ingredient,index) in 15" :key="'ingredient-'+index" v-if="drink['strIngredient'+index]">
              <div class="mr-2">{{ index }}.</div>
              <div class="d-flex align-items-center">
                {{ drink['strIngredient'+index] }}
              </div>
            </div>
          </div>
          <div class="mb-2">
            <h3>Measures</h3>
            <hr style="background-color: white; margin-top: 0">
            <div class="">
              <div class="mb-2 mr-2 d-flex align-items-center" v-for="(ingredient,index) in 15" :key="'measure-'+index" v-if="drink['strMeasure'+index]">
                <div class="mr-2">{{ index }}.</div>
                <div class="">
                  {{ drink['strMeasure'+index] }} of {{ drink['strIngredient'+index] }}
                </div>
              </div>
            </div>
          </div>
          <div class="mb-4">
            <h3>Instructions</h3>
            <hr style="background-color: white; margin-top: 0">
            <div v-if="drink.strInstructions.split('.')[index].length > 1" class="mb-2 mr-2 d-flex align-items-center" v-for="(ingredient,index) in drink.strInstructions.split('.')" :key="'instruction-'+index">
              <div class="mr-2">{{ index+1 }}.</div>
              <div class="">
                {{ drink.strInstructions.split('.')[index] }}
              </div>
            </div>
          </div>
        </b-col>
<!--        :style="'background: url('+ drink.strDrinkThumb +')'"-->
        <b-col order="1" order-xl="2" class="d-flex justify-content-center align-items-center image-container" xl="6">
          <img class="mx-auto mx-lg-0 drink-image" :src="drink.strDrinkThumb"/>
        </b-col>
        <b-button v-if="drink.strVideo" variant="warning" class="scroll-button" @click="scrollToElement">
          <img src="/chevron-down.svg" style="filter: invert(100%); height: 18px"  alt=""></b-button>
      </b-row>
    </b-container>
    <div v-if="drink.strVideo" class="video-holder text-center">
      <div>
        <h1 class="video-title">Tutorial Video</h1>
        <div style="border-radius: 14px; overflow: hidden; box-shadow: 2px 2px 18px black;">
          <client-only>
            <youtube class="video-player" style="width: 80vw; height: 80vh;" player-width="100%" player-height="100%" :mute="true" :player-vars="{ autoplay: 1 }" :video-id="$youtube.getIdFromURL(drink.strVideo)"></youtube>
          </client-only>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "drink",
  layout: 'drinks',
  data() {
    return {
      drink: null,
    }
  },
  mounted() {
    this.drink = JSON.parse(localStorage.getItem('selectedDrink'))
  },
  methods: {
    scrollToElement() {
      const el = this.$el.getElementsByClassName('video-holder')[0];

      if (el) {
        el.scrollIntoView({behavior: "smooth"});
      }
    }
  }
}
</script>

<style scoped>
@media only screen and (max-width: 700px) {
  .scroll-button {
    display: none;
  }
  .video-holder {
    height: auto !important;
    display: block !important;
    text-align: left !important;
    padding: 2rem 15px;
  }
  .left-side {
    padding-left: 15px !important;
    padding-top: 2rem;
  }
  .video-title {
    font-size: 28px !important;
    margin-bottom: 2rem !important;
  }
  .row-row {
    height: auto !important;
  }
  .drink-image {
    height: auto !important;
    width: 98% !important;
    margin: 0 !important;
  }
  .image-container {
    margin-bottom: 0 !important;
    margin-top: 1rem !important;
  }
}
@media only screen and (max-width: 1200px) {
  .video-player {
    height: 60vw !important;
    width: 90vw !important;
  }
  .image-container {
    padding-top: 1rem !important;
    margin-bottom: 2rem;
  }
}
@media only screen and (min-width: 701px) {
  .container-itself {
    height: 93%;
  }
}
.row-row {
  height: 100%;
}
.video-title {
  margin-bottom: 4rem;
}
.main-container {
  color: white;
  height: 100vh;
}
.drink-image {
  height: 500px;
  border-radius: 12px;
  box-shadow: 2px 2px 18px black;
}
/*.image-container {*/
/*  background-repeat: no-repeat !important;*/
/*  background-size: cover !important;*/
/*}*/
.left-side {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-left: 2rem;
}
.ingredient {
  background-color: #ffb700;
  padding: 4px 12px;
  border-radius: 50%;
  white-space: nowrap;
}
.video-holder {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.scroll-button {
  color:white;
  position: absolute;
  bottom: 5%;
  left: 50%;
  transform: translate(-50%,-5%);
  border-radius: 50%;
  padding-top: 8px;
  padding-bottom: 8px;
}
</style>
