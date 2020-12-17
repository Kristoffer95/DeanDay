<template>
  <b-container fluid>
    <Slick id="shop-slider" class="slider m-0 p-0">
      <div class="games">
        <h1 data-animation-in="fadeInUp" data-delay-in="0.2">
          {{ $route.params.name.replace(/-/g, ' ') }}
        </h1>
      </div>
    </Slick>
  </b-container>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.games {
  padding-top: 50px;
  min-height: calc(100vh - 270px);

  h1 {
    text-align: center;
    font-size: 34px;
  }
}
</style>
