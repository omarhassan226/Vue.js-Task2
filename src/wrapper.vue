<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <Header></Header>
      </div>
    </div>
    <div class="row d-flex justify-content-between">
      <div class="col-3">
        <Links></Links>
      </div>
      <div class="col-9">
        <Body></Body>
      </div>
    </div>
    <div class="row">
      <div class="col-md-12">
        <Footer></Footer>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import Links from './components/Links.vue';
import Body from './components/Body.vue';

export default {
  components: {
    Header,
    Footer,
    Links,
    Body
  }
}
</script>

<style>
.d-flex {
  display: flex;
}
</style>
