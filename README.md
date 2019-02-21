# Vue Timepiece

A time picker (year|day|hour|minute|second) for **Vue 2.x**, with flexible time format support.

## Demo

You can see the **Vue2 Timepicker** in action in the [Demo Page](https://asuralel.github.io/Asuralel.github.io-vue2-timepiece/)

## Github

[On click go to github](https://github.com/Asuralel/vue-timepiece) for basic guidelines.

## Dependencies

[Vue.js](http://vuejs.org/) v2.0+

## Installation

Through NPM **(Recommended)**

```bash
npm install vue-timepiece --save
```

Bower

```bash
bower install vue-timepiece --save
```

## Get Started

**Step 1:** Import vueTimepiece

**A**: Include the single file component **(Recommended)**

```javascript
// import
import vueTimepiece from 'vue-timepiece'

// Or, require
var vueTimepiece = require('vue-timepiece')

```

**Step 2**: Include VueTimepicker in your component

```javascript
var yourComponent = new Vue({
  components: { vueTimepiece },
  ...
})
```

**Step 3**: Then, you can introduce the `vue-timepicker` tag anywhere you like in your component's template


## Usage

### Basic Usage

```html
<!-- Default to 24-Hour format HH:mm -->
<vue-timepicker :doStart="doStart"></vue-timepicker>
```

### Customized Time Format

```html
<!-- Show seconds picker -->
<vue-timepicker format="hh:mm:ss"></vue-timepicker>

```

VueTimepicker will recognizes the following tokens in the format string

Section    | Token | Output
---------- | ----- | ---------------
**Year**   | yy    | 01 02 ...
**Month**  | MM    | 01 02 ... 11 12
**Day**    | dd    | 01 02 ... 29 30
**Hour**   | hh    | 01 02 ... 11 12
**Minute** | mm    | 00 01 ... 58 59
**Second** | ss    | 00 01 ... 58 59

> If not set, `format` string will be default to "hh:mm:ss"

```

## Props API

Prop                  | Type      | Required | Default Value
--------------------- | --------- | -------- | -------------
**doStart**           | _Boolean_ | yes      | false
**format**            | _String_  | no       | "hh:mm:ss"
**showTimeString**    | _Boolean_ | no       | true

## Function API

Function Name         | Return
--------------------- | ---------
**finishTime**        | Time String

## Contribution

Please feel free to fork and help developing.

## License

[ISC]