# vue-snb-slider

vue-snb-slider is a slider componen for Vue.js.

[![GitHub stars](https://img.shields.io/github/stars/cherislive/vue-snb-slider.svg?style=flat-square)](https://github.com/cherislive/vue-snb-slider/stargazers)
[![Build Status](https://travis-ci.org/cherislive/vue-snb-slider.svg?branch=master)](https://travis-ci.org/cherislive/vue-snb-slider)
[![GitHub issues](https://img.shields.io/github/issues/cherislive/vue-snb-slider.svg?style=flat-square)](https://github.com/cherislive/vue-snb-slider/issues)
[![GitHub forks](https://img.shields.io/github/forks/cherislive/vue-snb-slider.svg?style=flat-square)](https://github.com/cherislive/vue-snb-slider/network)
[![GitHub last commit](https://img.shields.io/github/last-commit/google/skia.svg?style=flat-square)](https://github.com/cherislive/vue-snb-slider)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square)](https://github.com/cherislive/vue-snb-slider)
[![NPM](https://nodei.co/npm/vue-snb-slider.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/vue-snb-slider/)
[![NPM](https://nodei.co/npm-dl/vue-snb-slider.png?months=9&height=3)](https://nodei.co/npm/vue-snb-slider/)



## Mobile demo

![https://cherislive.github.io/projrct/vue-snb-slider/](./dist/20190321-173707.png)

## Install

```bash
$ npm install vue-snb-slider
```

## Import

### Import using module

Import components to your project:

``` js
// in ES6 modules
import { Slider, SliderItem } from 'vue-snb-slider';

// in CommonJS
const { Slider, SliderItem } = require('vue-snb-slider');

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
<script src="../node-modules/vue-snb-slider/dist/vue-snb-slider.js"></script>
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
