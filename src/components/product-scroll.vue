<script setup>
import { ProductCard } from "np-product-card";
import "np-product-card/styles.css";
</script>
<template>
  <div class="product-slider" ref="slider">
    <div class="product-slider__inner" ref="inner" :style="innerStyles">
      <product-card
        v-for="(item, index) in productSlider"
        :key="index"
        :type="item.type"
        :size="item.size"
      />
    </div>
  </div>
  <button v-if="showPrev" type="button" class="arrow-prev" @click="productPrev">
    &lsaquo;
  </button>
  <button v-if="showNext" type="button" class="arrow-next" @click="productNext">
    &rsaquo;
  </button>
</template>

<style scoped>
.product-slider {
  width: 100%;
  position: relative;
  overflow: hidden;
}
.product-slider__inner {
  display: flex;
  align-items: start;
  transition: transform 0.2s;
  white-space: nowrap;
}
.arrow-prev,
.arrow-next {
  cursor: pointer;
  border-radius: 100%;
  text-align: center;
  width: 40px;
  height: 40px;
  -webkit-box-shadow: 0 0 24px -4px rgb(0 0 0 / 24%);
  box-shadow: 0 0 24px -4px rgb(0 0 0 / 24%);
  background-color: #ffffff;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  position: absolute;
  top: 50%;
  margin-top: -40px;
  z-index: 1;
  font-size: 30px;
  color: #0095DA;
  border: 0;
}
.arrow-prev {
  left: -20px;
}
.arrow-next {
  right: -20px;
}
@media (max-width: 768px) {
  .arrow-next,
  .arrow-prev {
    font-size: 20px;
    width: 25px;
    height: 25px;
    margin-top: -25px;
  }
  .arrow-prev {
    left: -12px;
  }
  .arrow-next {
    right: -12px;
  }
}
</style>

<script scoped>
export default {
  data() {
    return {
      //state
      scrollAmount: 0,
      showPrev: false,
      showNext: true,
      innerStyles: "",
      scTimer: 0,
      scY: 0,
      //productSlider data
      productSlider: [
        {
          size: "",
          type: "",
        },
        {
          size: "",
          type: "disabled",
        },
        {
          size: "",
          type: "",
        },
        {
          size: "",
          type: "",
        },
        {
          size: "",
          type: "disabled",
        },
        {
          size: "",
          type: "",
        },
        {
          size: "",
          type: "",
        },
        {
          size: "small",
          type: "",
        },
      ],
    };
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  methods: {
    productNext: function () {
      this.showPrev = true;
      const inner = this.$refs.inner;
      const newScrollLeft = inner.scrollLeft;
      const width = inner.clientWidth;
      const scrollWidth = inner.scrollWidth;
      this.scrollAmount += 30;

      this.innerStyles = {
        transform: `translateX(-${this.scrollAmount}px)`,
      };

      if (scrollWidth - width < this.scrollAmount) {
        this.showNext = false;
        this.innerStyles = {
          transform: `translateX(-${scrollWidth - width}px)`,
        };
      }
    },
    productPrev: function () {
      this.showNext = true;
      const inner = this.$refs.inner;
      const newScrollLeft = inner.scrollLeft;
      const width = inner.clientWidth;
      const scrollWidth = inner.scrollWidth;
      this.scrollAmount -= 30;

      this.innerStyles = {
        transform: `translateX(-${this.scrollAmount}px)`,
      };

      if (this.scrollAmount <= 0) {
        this.showPrev = false;
      }
    },
    handleScroll: function () {
      if (this.scTimer) return;
      this.scTimer = setTimeout(() => {
        this.scY = window.scrollY;
        clearTimeout(this.scTimer);
        this.scTimer = 0;
      }, 100);
    },
  },
};
</script>