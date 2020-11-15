# VueRangedatePicker

[![npm](https://img.shields.io/npm/v/vue-rangedate-picker-winslow.svg)](https://www.npmjs.com/package/vue-rangedate-picker-winslow)
[![vue2](https://img.shields.io/badge/vue-2.x-brightgreen.svg)](https://vuejs.org/) 


> Vue Date picker with range selection

## Demo

[https://bliblidotcom.github.io/vue-rangedate-picker/demo/](https://bliblidotcom.github.io/vue-rangedate-picker/demo/)

## Installation

```bash
npm install --save vue-rangedate-picker-winslow
```

## Usage

### Bundler (Webpack, Rollup)

```js
import Vue from 'vue'
import VueRangedatePicker from 'vue-rangedate-picker-winslow'

Vue.use(VueRangedatePicker)
```

### Browser

```html
<!-- Include after Vue -->
<!-- Local files -->
<script src="vue-rangedate-picker-winslow/dist/vue-rangedate-picker.min.js"></script>

<!-- From CDN -->
<script src="https://unpkg.com/vue-rangedate-picker-winslow"></script>
```

### Available Events

You can catch these below Events to `<vue-rangedate-picker @events="events"></vue-rangedate-picker>` template :

+ **selected**

  *Description* : function that will `$emit` when datepicker set value, this function will get parameter response :
  ```javascript
  {
    start: new Date(2018, 05, 01)
    end: new Date(2018, 05, 31)
  }
  ```

### Available Props

You can pass these below props to `<vue-rangedate-picker :props="props"></vue-rangedate-picker>` template :

+ **configs**

  *Description* : -

  *Type* : Object

  *Default Value* : `{}`

+ **i18n**

  *Description* : For text translation (currently: ID/EN)

  *Type* : String

  *Default Value* : `'EN'`

  *Component Example* : `<vue-rangedate-picker i18n="ID" />`

+ **months**

  *Description* : Array of months name

  *Type* : Array

  *Default Value* : 
  ```javascript
  EN: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
  ID: ['Januari', 'Februari', 'Maret', 'April', 'Mei', 'Juni', 'Juli', 'Agustus', 'September', 'Oktober', 'November', 'Desember']
  ```

  *Component Example* : `<vue-rangedate-picker :months="['Enero', 'Febrero', 'Marzo', ...]" />`

+ **shortDays**

  *Description* : Array of days name in short

  *Type* : Array

  *Default Value* : 
  ```javascript
  EN: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'],
  ID: ['Min', 'Sen', 'Sel', 'Rab', 'Kam', 'Jum', 'Sab']
  ```

+ **captions**

  *Description* : Object for text title and OK button

  *Type* : Object

  *Default Value* : 
  ```javascript
  {
    'title': 'Choose Dates',
    'ok_button': 'Apply'
  }
  ```

+ **format**

  *Description* : Date format

  *Type* : String

  *Default Value* : `'DD MMM YYYY'`

  *Component Example* : `<vue-rangedate-picker months="YYYY-MM-DD" />`

+ **styles**

  *Description* : -

  *Type* : Object

  *Default Value* : 
  ```javascript
  {
    daysWeeks: 'calendar_weeks',
    days: 'calendar_days',
    daysSelected: 'calendar_days_selected',
    daysInRange: 'calendar_days_in-range',
    firstDate: 'calendar_month_left',
    secondDate: 'calendar_month_right',
    presetRanges: 'calendar_preset-ranges'
  }
  ```

+ **initRange**

  *Description* : Initial date range (start date & end date) for date range picker.

  *Type* : Object

  *Default Value* : `null`

  Example Object : 
  ```javascript
  {
    start: new Date(this.initRange.start),
    end: new Date(this.initRange.end)
  }
  ```


  *Component Example* : `<vue-rangedate-picker :initRange="initialRange" />`
  ```
  // initial 7 day range
  const n = new Date();
  const start = new Date(n.getFullYear(), n.getMonth(), n.getDate() - 5);
  const end = new Date(n.getFullYear(), n.getMonth(), n.getDate() + 1);
  {
    start: start,
    end: end
  }
  ```

+ **startActiveMonth**

  *Description* : Month will be shown in first launch

  *Type* : Number

  *Default Value* : `new Date().getMonth()`

+ **startActiveYear**

  *Description* : Year will be shown in first launch

  *Type* : Number

  *Default Value* : `new Date().getFullYear()`

+ **presetRanges**

  *Description* : Set of objects that will shown as quick selection of daterange

  *Type* : Object

  Example Object : 
  ```javascript
  {
    today: function () {
      const n = new Date()
      const startToday = new Date(n.getFullYear(), n.getMonth(), n.getDate() + 1, 0, 0)
      const endToday = new Date(n.getFullYear(), n.getMonth(), n.getDate() + 1, 23, 59)
      return {
        label: presetRangeLabel[i18n].today,
        active: false,
        dateRange: {
          start: startToday,
          end: endToday
        }
      }
    }
  }
  ```

  *Default Value* : 
  ```javascript
  {
    today: function () {
      return {
        // label: 'string', active: 'boolean', dateRange: {start: date, end: end}
      }
    },
    thisMonth: function () {},
    lastMonth: function () {},
    last7days: function () {},
    last30days: function () {}
  }
  ```

+ **compact**

  *Description* : Set to `'true'` if you want to make datepicker always shown in compact mode

  *Type* : String

  *Default Value* : `'false'`

+ **righttoleft**

  *Description* : Set to `'true'` if you want datepicker shown align to `right`

  *Type* : String

  *Default Value* : `'false'`

## Development

### Launch visual tests

```bash
npm run dev
```

### Launch Karma with coverage

```bash
npm run dev:coverage
```

### Build

Bundle the js and css of to the `dist` folder:

```bash
npm run build
```


## Publishing

The `prepublish` hook will ensure dist files are created before publishing. This
way you don't need to commit them in your repository.

```bash
# Bump the version first
# It'll also commit it and create a tag
npm version
# Push the bumped package and tags
git push --follow-tags
# Ship it 🚀
npm publish
```

## License

[MIT](http://opensource.org/licenses/MIT)
