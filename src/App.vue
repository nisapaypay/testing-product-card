<script setup>
  import Header from './components/header.vue'
  import ProductScroll from './components/product-scroll.vue'
  import Footer from './components/footer.vue'
</script> 

<template>
  <Header />
  <section>
    <div class="container">
      <div class="flex-area">
        <div class="horizontal-box">
          <div class="yellow-box">
            <h3>1</h3>
          </div>
          <div class="blue-box">
            <h3>2</h3>
          </div>
        </div>
        <div class="purple-box">
          <h3>3</h3>
        </div>
        <div class="pink-box">
          <h3>4</h3>
        </div>
        <div class="slider-box">
          <ProductScroll />
        </div>
      </div>
    </div>
  </section>
  <Footer />
</template>

<style scoped>
.flex-area {
  display: flex;
  display: -ms-flexbox;
  flex-direction: column;
    -moz-box-direction: column;
    -webkit-box-direction: column;
  flex-wrap: wrap;
    -ms-flex-wrap: wrap;
}
.horizontal-box {
  display: -webkit-box;
  max-width: 100%;
}
.yellow-box,
.blue-box,
.purple-box,
.pink-box {
  display: flex;
  display: -ms-flexbox;
    -webkit-box-align: center;
    -ms-flex-align: center;
  align-items: center;
    -webkit-box-pack: center;
    -ms-flex-pack: center;
  justify-content: center;
  max-width: 100%;
  margin: 0.5rem 0px;
  min-height: 200px;
  font-size: 4rem;

}
.yellow-box{
  background-color: #dbfa3a;
    -ms-flex: 0 0 calc(50% - 0.5rem);
  flex: 0 0 calc(50% - 0.5rem);
  margin-right: 0.5rem;
}
.blue-box {
  background-color: #3cf2fc;
    -ms-flex: 0 0 calc(50% - 0.5rem);
  flex: 0 0 calc(50% - 0.5rem);
  margin-left: 0.5rem;
}
.purple-box {
  background-color: #f379fd;
}
.pink-box {
  background-color: #fd8b8c;
}
.slider-box {
  position: relative;
  margin-top: 0.5rem;
  max-width: 100%;
}

@media(max-width: 768px) {
  .horizontal-box{
    order: 4;
  }
  .slider-box {
    order: 3;
  }
  .purple-box {
    order: 2;
  }
  .pink-box {
    order: 1;
  }
}
</style>
