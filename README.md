## What is this repo?
This repo is to solve jQuery import errors at [godbasin/vue-select2](https://github.com/godbasin/vue-select2)

Example:
```
Uncaught SyntaxError: The requested module '/node_modules/jquery/dist/jquery.js?v=12345' does not provide an export named 'default'
```

```
TypeError: Abc(...).find(...).select2 is not a function
```

```
ReferenceError: $ is not defined
```

## What are the code changes?

I removed all about jQuery and Select2 import, but you need to import jQuery and Select2 manually from CDN etc.

## Requirements
- Vite
- Vue version: 3.x or later
- jQuery version: any **(CDN)**
- Select2 version: 4.x or later **(CDN)**

If you install jQuery and Select2 using npm, it may not work well.

## How to use 

#### 1. Install
```
npm install xignp/vue3-select2-component#v1.0.0
```
I'm not publishing this package in npm, So npm will install this package from github.

#### 2. Import jQuery and Select2

index.html or xxx.blade.php or etc..

``` html
<script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/select2/4.0.13/js/select2.min.js"></script>
<link
  href="https://cdnjs.cloudflare.com/ajax/libs/select2/4.0.13/css/select2.min.css"
  rel="stylesheet"
/>
```
[jQueryCDN](https://releases.jquery.com/)

[Select2CDN](https://cdnjs.com/libraries/select2)

#### 4. Use as Component

Sample.vue
``` vue
<script setup>
import Select2 from "vue3-select2-component";
</script>

<template>
  <div>
    <Select2 />
  </div>
</template>

<style scoped></style>
```

## Full Sample

index.html
``` html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <script
      src="https://code.jquery.com/jquery-3.7.1.min.js"
      integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo="
      crossorigin="anonymous"
    ></script>
    <link
      href="https://cdnjs.cloudflare.com/ajax/libs/select2/4.0.13/css/select2.min.css"
      rel="stylesheet"
    />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/select2/4.0.13/js/select2.min.js"></script>
    <title>Vite + Vue</title>
  </head>
  <body>
    <div id="app"></div>
    <script type="module" src="/src/main.js"></script>
  </body>
</html>
```

App.vue
``` vue
<script setup>
import { ref } from "vue";
import Select2 from "vue3-select2-component";

const myValue = ref("Banana");
const myOptions = ref(["Apple", "Banana", "Orange"]);

const myChangeEvent = (val) => {
  console.log(val);
};

const mySelectEvent = ({ id, text }) => {
  console.log({ id, text });
};
</script>

<template>
  <div>
    <Select2
      v-model="myValue"
      :options="myOptions"
      :settings="{ dropdownAutoWidth: true, width: 'auto' }"
      @change="myChangeEvent($event)"
      @select="mySelectEvent($event)"
    />
    <h4>Value: {{ myValue }}</h4>
  </div>
</template>

<style scoped></style>
```

main.js
``` js
import { createApp } from "vue";
import "./style.css";
import App from "./App.vue";

createApp(App).mount("#app");
```


