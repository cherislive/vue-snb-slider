<template>
<div>
  <Slider style="width:300px; margin:20px auto;">
    <SliderItem class="base-slider-item">111</SliderItem>
    <SliderItem class="base-slider-item">222</SliderItem>
    <SliderItem class="base-slider-item">333</SliderItem>
    <SliderItem class="base-slider-item">444</SliderItem>
  </Slider>

  <Slider style="width:300px; margin:20px auto;"
    :showIndicators="false"
  >
    <SliderItem class="base-slider-item">111</SliderItem>
    <SliderItem class="base-slider-item">222</SliderItem>
    <SliderItem class="base-slider-item">333</SliderItem>
    <SliderItem class="base-slider-item">444</SliderItem>
  </Slider>

  <Slider style="width:300px; margin:20px auto;"
    :perView="2"
    :perGroup="1"
    :showIndicators="false"
  >
    <SliderItem class="base-slider-item">111</SliderItem>
    <SliderItem class="base-slider-item">222</SliderItem>
    <SliderItem class="base-slider-item">333</SliderItem>
    <SliderItem class="base-slider-item">444</SliderItem>
  </Slider>

  <Slider style="width:300px; margin:20px auto;"
    :perView="2"
    :perGroup="2"
    :showIndicators="false"
  >
    <SliderItem class="base-slider-item">111</SliderItem>
    <SliderItem class="base-slider-item">222</SliderItem>
    <SliderItem class="base-slider-item">333</SliderItem>
    <SliderItem class="base-slider-item">444</SliderItem>
    <SliderItem class="base-slider-item">555</SliderItem>
  </Slider>

  <Slider style="width:300px; margin:20px auto;"
    :perView="2.5"
    :perGroup="2"
    :showIndicators="false"
  >
    <SliderItem class="base-slider-item">111</SliderItem>
    <SliderItem class="base-slider-item">222</SliderItem>
    <SliderItem class="base-slider-item">333</SliderItem>
    <SliderItem class="base-slider-item">444</SliderItem>
    <SliderItem class="base-slider-item">555</SliderItem>
    <SliderItem class="base-slider-item">666</SliderItem>
    <SliderItem class="base-slider-item">777</SliderItem>
    <SliderItem class="base-slider-item">888</SliderItem>
  </Slider>

  <Slider style="width:300px; margin:20px auto; background:#eee;"
    :perView="5"
    :perGroup="5"
    :groupFull="true"
    :showIndicators="false"
  >
    <SliderItem class="base-slider-item">1</SliderItem>
    <SliderItem class="base-slider-item">2</SliderItem>
    <SliderItem class="base-slider-item">3</SliderItem>
    <SliderItem class="base-slider-item">4</SliderItem>
    <SliderItem class="base-slider-item">5</SliderItem>
    <SliderItem class="base-slider-item">6</SliderItem>
    <SliderItem class="base-slider-item">7</SliderItem>
    <SliderItem class="base-slider-item">8</SliderItem>
  </Slider>
</div>
</template>

<script>
  import { Slider, SliderItem } from '../src';

  export default {
    components: {
      Slider, SliderItem
    },
    data() {
      return {
        defaultDate: '',
      };
    },
    created() {
    },
    methods: {
    }
  };
</script>

<style>
.base-slider-item{height:100px; color:#fff; font-size:36px; line-height:100px; text-align:center; background:#ccc;}
</style>
