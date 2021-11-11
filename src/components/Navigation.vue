<template>
  <div class="nav row middle-md between-md">
    <div id="logo" class="col-md-2">
      <img src="@/assets/logo.png" alt="">
    </div>
    <div class="nav-list col-md-3 col-sm-4">
      <nav class="row between-md">
        <a href="">About site</a>
        <a href="">Resurce</a>
        <a href="">FAQ</a>
      </nav>
    </div>

    <div class="btn-list col-md-4">
      <nav class="row end-md">
        <a href="" class="btn">Exchange</a>
        <a href="" class="btn btn-outline">Contant</a>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navigation',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #logo img{
    height: 32px;
    width: 32px;
    object-fit: contain;
  }

  .btn-list a{
    margin-left: 24px;
  }
</style>
