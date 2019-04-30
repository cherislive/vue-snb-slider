# vue-dnb-slider

vue-dnb-slider is a slider componen for Vue.js.

[![GitHub stars](https://img.shields.io/github/stars/cherislive/vue-dnb-slider.svg?style=flat-square)](https://github.com/cherislive/vue-dnb-slider/stargazers)
[![Build Status](https://travis-ci.org/cherislive/vue-dnb-slider.svg?branch=master)](https://travis-ci.org/cherislive/vue-dnb-slider)
[![GitHub issues](https://img.shields.io/github/issues/cherislive/vue-dnb-slider.svg?style=flat-square)](https://github.com/cherislive/vue-dnb-slider/issues)
[![GitHub forks](https://img.shields.io/github/forks/cherislive/vue-dnb-slider.svg?style=flat-square)](https://github.com/cherislive/vue-dnb-slider/network)
[![GitHub last commit](https://img.shields.io/github/last-commit/google/skia.svg?style=flat-square)](https://github.com/cherislive/vue-dnb-slider)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square)](https://github.com/cherislive/vue-dnb-slider)
[![NPM](https://nodei.co/npm/vue-dnb-slider.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/vue-dnb-slider/)
[![NPM](https://nodei.co/npm-dl/vue-dnb-slider.png?months=9&height=3)](https://nodei.co/npm/vue-dnb-slider/)



## Mobile demo

![https://cherislive.github.io/projrct/vue-dnb-slider/](./dist/20190321-173707.png)

## Install

```bash
$ npm install vue-dnb-slider
```

## Import

### Import using module

Import components to your project:

``` js
// in ES6 modules
import { Slider, SliderItem } from 'vue-dnb-slider';

// in CommonJS
const { Slider, SliderItem } = require('vue-dnb-slider');

// in Global variable
const { Slider, SliderItem } = VueSnbSlider;
```

And register components:

``` js
Vue.component('slider', Slider);
Vue.component('slider-item', SliderItem);
```

### Import using script tag

``` html
<script src="../node-modules/vue-dnb-slider/dist/vue-dnb-slider.js"></script>
```

``` js
const vueSlider = VueSnbSlider.Slider;
const vueSliderItem = VueSnbSlider.SliderItem;

new Vue({
  el: 'body',
  components: {
    'slider': vueSlider,
    'slider-item': vueSliderItem
  }
});
```

## Usage

Work on a Vue instance:

```HTML
<slider>
  <slider-item>slider1</slider-item>
  <slider-item>slider2</slider-item>
  <slider-item>slider3</slider-item>
</slider>
```
## Slider Options

### Props

| Option | Type | Description | Default |
| ----- | ----- | ----- | ----- |
| perView | Number | Number of slides per view (min:1). | 1 |
| perGroup | Number | Set numbers of slides to define and enable group sliding. Useful to use with perView >= perGroup | 1 |
| groupFull | Boolean | --- | false |
| showIndicators | Boolean | Show indicators on slider bottom | true |

### Events

| Event Name | Description | params |
| ----- | ----- | ----- |
| change | triggers when current slider-item change | new slider item Index |

## SliderItem Options

### Props

| Option | Type | Description | Default |
| ----- | ----- | ----- | ----- |
| item | Object | -- | -- |

### Events

| Event Name | Description | params |
| ----- | ----- | ----- |
| sliderItemOnClick | triggers when click slider-item | Props item: {}  |

## Development

Watching with hot-reload:

```bash
$ npm run dev
```

Develop on real remote device:

```bash
$ npm run remote-dev {{ YOUR IP ADDRESS }}
```

## License

MIT
