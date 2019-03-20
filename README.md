# vue-mint-slider

vue-mint-slider is a slider componen for Vue.js.

## Install

```bash
$ npm install vue-mint-slider
```

## Import

### Import using module

Import components to your project:

``` js
require('vue-mint-slider/dist/vue-mint-slider.css');

// in ES6 modules
import { Slider, SliderItem } from 'vue-mint-slider';

// in CommonJS
const { Slider, SliderItem } = require('vue-mint-slider');

// in Global variable
const { Slider, SliderItem } = VueMintSlider;
```

And register components:

``` js
Vue.component('slider', Slider);
Vue.component('slider-item', SliderItem);
```

### Import using script tag

``` html
<link rel="stylesheet" href="../node-modules/vue-mint-slider/dist/vue-mint-slider.css" charset="utf-8">
<script src="../node-modules/vue-mint-slider/dist/vue-mint-slider.js"></script>
```

``` js
const vueSlider = VueMintSlider.Slider;
const vueSliderItem = VueMintSlider.SliderItem;

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
## Options

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
