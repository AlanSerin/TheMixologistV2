<template>
  <b-container>
    <b-row>
      <b-col>
        <div class="body-holder text-center mt-4">
          <h1 class="search-title">Search Drinks</h1>
          <div class="search-text">Select category, type what you're looking for then hit enter</div>

          <SearchBar />
        </div>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: 'search',
}
</script>
<style lang="css">
@media only screen and (max-width: 750px) {
  .search-title {
    font-size: 2.5rem !important;
  }
  .search-text {
    font-size: 1rem !important;
    width: 100% !important;
    margin-bottom: 1.25rem !important;
  }
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
.body-holder {
  color: white;
  flex: 1;
  overflow: auto;
}
.search-title {
  font-size: 5rem;
}
.search-text {
  font-size: 1.50rem;
  margin-bottom: 2.5rem;
}
</style>
