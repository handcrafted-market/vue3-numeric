# vue3-numeric

[![npm](https://img.shields.io/npm/v/vue3-numeric.svg?style=flat-square)](https://www.npmjs.com/package/@handcrafted-market/vue3-numeric)
[![npm](https://img.shields.io/npm/dt/vue3-numeric.svg?style=flat-square)](https://www.npmjs.com/package/@handcrafted-market/vue3-numeric)
[![npm](https://img.shields.io/npm/dm/vue3-numeric.svg?style=flat-square)](https://www.npmjs.com/package/@handcrafted-market/vue3-numeric)

This is an implementation for Vue 3 of the Original project [vue-numeric](https://github.com/kevinongko/vue-numeric) in its version 2.4.3.

It initially existed at https://github.com/flvportafolio/vue3-numeric but seems to have been deleted. Since it has an MIT license, it's been reuploaded here in the state that it last existed in our deployments. We may or may not be able to actually support issues that are raised for the project.

## Installation

```sh
# NPM
$ npm install @handcrafted-market/vue3-numeric
```
## CDN
```html
<html>
  <head>
    <script src="https://unpkg.com/vue@next"></script>
  </head>
  <body>
    <div id="app">
       {{price}}
      <hr>
      <vue-numeric
        currency="$"
        separator=","
        v-model="price"
        :precision="2"
      ></vue-numeric>
    </div>
    <script src="https://unpkg.com/vue3-numeric@1.0.1/dist/vue3-numeric.umd.js"></script>
    <script type="module">
      const VueNumeric = window["vue3-numeric"];
      Vue.createApp({
        setup() {
          const price = Vue.ref("123");
          return { price };
        }
      })
      .component("vue-numeric", VueNumeric)
      .mount("#app");
    </script>
  </body>
</html>
```
#### Register globally

```js
import { createApp } from 'vue';
import App from './App.vue';
import VueNumeric from 'vue3-numeric';

createApp(App)
  .component("vue-numeric", VueNumeric)
  .mount('#app');
```

#### Register as Component (Composition Api)

```html
<script>
import { ref } from 'vue';
import VueNumeric from 'vue3-numeric';
export default {
  components: { VueNumeric },
  setup() {
    const price = ref('');
    return { price };
  },
};
</script>
<template>
  <vue-numeric
    separator=","
    v-model="price"
    :precision="2"
  ></vue-numeric>
</template>
```

#### Register as Component (Composition Api - setup sugar)

```html
<script setup>
import { ref } from 'vue';
import VueNumeric from 'vue3-numeric';
const price = ref('');
</script>
<template>
  <vue-numeric
    separator=","
    v-model="price"
    :precision="2"
  ></vue-numeric>
</template>
```


## Usage

### Quick example
```vue
<script>
import { ref } from 'vue';
import VueNumeric from 'vue3-numeric';
export default {
  components: { VueNumeric },
  setup() {
    const price = ref('');
    return { price };
  },
};
</script>
<template>
  <vue-numeric
    currency="$" 
    separator=","
    v-model="price"
    :precision="2"
  ></vue-numeric>
</template>
```

### Currency symbol

Set the `currency` prop to add a currency symbol within the input.

```vue
<vue-numeric currency="$"></vue-numeric>
```
### Currency symbol Spacing

Set the `currencySymbolSpacing` prop to false to show `$2.00.` instead of `$ 2.00`.
By default the value is true

```vue
<vue-numeric
  currency="$"
  :currencySymbolSpacing="false"
></vue-numeric>
```

### Minimum & maximum constraint

Limit the minimum and maximum value by using `min` and `max` props.

- `min` defaults to `0`.
- `min` and `max` accept `String` or `Number` values.

```vue
<vue-numeric v-bind:min="2000" v-bind:max="10000"></vue-numeric>
```

### Disable/enable negative values

`minus` defaults to `false` (no negative numbers).

```vue
<vue-numeric v-bind:minus="false"></vue-numeric>
```

### Enable decimal precision

By default the decimal value is disabled. To use decimals in the value, add the `precision` prop.
- `precision` accept a `String` or `Number` numeric value.

```vue
<vue-numeric v-bind:precision="2"></vue-numeric>
```

### Thousands separator
- Default thousand separator's symbol is `,`.
- Use the `separator` prop to change the thousands separator.
- `separator` only accepts `space`, `,` or `.`.
- When using the `.` or `space` as thousand separator, the decimal separator will be `,`.

```vue
<vue-numeric separator="."></vue-numeric>
```


### Input placeholder when empty
```vue
<vue-numeric placeholder="only number allowed"></vue-numeric>
```

### Value when empty
By default, when you clean the input the value is set to `0`. You can change this value to fit your needs.
```vue
<vue-numeric :empty-value="1"></vue-numeric>
```

### Output Type
By default the value emitted for the input event is of type `Number`. However you may choose to get a `String` instead
by setting the property `output-type` to `String`.
```vue
<vue-numeric output-type="String"></vue-numeric>
```

## Props
|Props|Description|Required|Type|Default|
|-----|-----------|--------|----|-------|
|currency|Currency prefix|false|String|-|
|currency-symbol-position|Position of the symbol (accepted values: `prefix` or `suffix`)|false|String|`prefix`|
|max|Maximum value allowed|false|Number|9007199254740991|
|min|Minimum value allowed|false|Number|-9007199254740991|
|minus|Enable/disable negative values|false|Boolean|`false`|
|placeholder|Input placeholder|false|String|-|
|empty-value|Value when input is empty|false|Number|0|
|output-type|Output Type for input event|false|String|`String`|
|precision|Number of decimals|false|Number|-|
|separator|Thousand separator symbol (accepts `space`, `.` or `,`)|false|String|`,`|
|decimal-separator|Custom decimal separator|false|String|-|
|thousand-separator|Custom thousand separator|false|String|-|
|read-only|Hide input field and show the value as text|false|Boolean|false|
|read-only-class|Class for read-only element|false|String|''|

## License
[MIT license](http://opensource.org/licenses/MIT)

## Recommended IDE Setup

- [VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar)
