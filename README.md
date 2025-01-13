# jets-seatmap-vue-wrapper

## Installation and integration

Add as dependency to `package.json` and run `npm install'

```json
"dependencies": {
    ...
     "jets-seatmap-vue-wrapper": "github:Kwiket/jets-seatmap-vue-wrapper"
    ...
  },
```

Import and use component in `main.js` file

`FOR VUE 2.x`

```js
import Vue from 'vue';
import App from './App.vue';

// import and use, component will register itself
import JetsSeatmap from 'jets-seatmap-vue-wrapper';
Vue.use(JetsSeatmap);

Vue.config.productionTip = false;

new Vue({
  render: (h) => h(App),
}).$mount('#app');
```

`FOR VUE 3.x`

```js
import { createApp } from 'vue';
import App from './App.vue';

import JetsSeatmap from 'jets-seatmap-vue-wrapper';

const app = createApp(App);

// difference in "use" between 2.x and 3.x
app.use(JetsSeatmap);

app.mount('#app');
```

Use the `JetsSeatmap` in your component

```js
<template>
  <div id="app">
    <JetsSeatmap
      :flight="flight"
      :config="config"
      :availability="availability"
      :passengers="passengers"
      :seatJumpTo="seatJumpTo"
      :currentDeckIndex="currentDeckIndex"
      @onSeatMapInited="onSeatMapInited($event)"
      @onSeatSelected="onSeatSelected($event)"
      @onSeatUnselected="onSeatUnselected($event)"
      @onTooltipRequested="onTooltipRequested($event)"
      @onLayoutUpdated="onLayoutUpdated($event)"
      @onSeatMouseLeave="onSeatMouseLeave($event)"
      @onSeatMouseClick="onSeatMouseClick($event)"
      @onAvailabilityApplied="onAvailabilityApplied($event)"
    ></JetsSeatmap>
  </div>
</template>
```

Change `config_mock.js`:

```
apiUrl: 'PROVIDED_API_URL',
apiAppId: 'PROVIDED_APP_ID',
apiKey: 'PROVIDED_API_KEY',

```

`replace all PROVIDED_VALUES` with your credentials.

```js
<script>
import FLIGHT_MOCK from "./mock-data/flight_mock";
import CONFIG_MOCK from "./mock-data/config_mock";
import AVAILABILITY_MOCK from "./mock-data/availability_mock";
import PASSENGERS_MOCK from "./mock-data/passangers_mock";
import SEAT_JUMP_TO_MOCK from "./mock-data/seat_jump_to_mock";

const CURRENT_DECK_INDEX = 0;

export default {
  name: "App",

  methods: {
    onSeatMapInited(data) {
      console.log("onSeatMapInited", data);
    },
    onSeatSelected(data) {
      console.log("onSeatSelected", data);
    },
    onSeatUnselected(data) {
      console.log("onSeatUnselected", data);
    },
    onTooltipRequested(data) {
      console.log("onTooltipRequested", data);
    },
    onLayoutUpdated(data) {
      console.log("onLayoutUpdated", data);
    },
    onSeatMouseLeave(data) {
      console.log("onSeatMouseLeave", data);
    },
    onSeatMouseClick(data) {
      console.log("onSeatMouseClick", data);
    },
    onAvailabilityApplied(data) {
      console.log("onAvailabilityApplied", data);
    },
  },

  data() {
    return {
      flight: FLIGHT_MOCK,
      config: CONFIG_MOCK,
      passangers: PASSENGERS_MOCK,
      availability: AVAILABILITY_MOCK,
      seatJumpTo: SEAT_JUMP_TO_MOCK,
      currentDeckIndex: CURRENT_DECK_INDEX,
    };
  },
};
</script>

```

For better undertanding how it works read [React lib doc](https://github.com/Kwiket/jets-seatmap-react-lib-pub) and [Integration instruction](https://github.com/Kwiket/jets-seatmap-react-lib-pub/blob/version-2/SEATMAP-INTEGRATION.md)
