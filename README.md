# getBaseline.js
A script for getting the information about baseline of web fonts

## Usage
```javascript
var baseline = getBaseline(font, sizeRange, elem);
```
- **font**  
   Type: string  
   Default: Computed font family of the element  
   A string of font family.
- **sizeRange**  
   Type: array  
   Default: `[11, 110]`  
   An array has min and max font size `[min, max]` or one font size `[n]`
- **elem**  
   Type: element  
   Default: document.body  
   The element of the document at which the test should be done.

### Basic
**JS**
```javascript
var baseline = getBaseline();
```
**Returns**
```json
{
  "font-family": "Apple SD Gothic Neo",
  "font-size-range": [
    11,
    110
  ],
  "baseline-ratio": 0.2139939328432772,
  "data": [
    {
      "font-size": "11px",
      "baseline-offset": "9px",
      "baseline-height": "2px",
      "baseline-ratio": 0.18181818181818182
    },
    ...
    {
      "font-size": "110px",
      "baseline-offset": "88px",
      "baseline-height": "22px",
      "baseline-ratio": 0.2
    }
  ]
}
```

### Web Safe Fonts
**JS**
```javascript
var baseline = getBaseline('Times New Roman');
```
**Returns**
```json
{
  "font-family": "Times New Roman",
  "font-size-range": [
    11,
    110
  ],
  "baseline-ratio": 0.17501037235545686,
  "data": [
    {
      "font-size": "11px",
      "baseline-offset": "9px",
      "baseline-height": "2px",
      "baseline-ratio": 0.18181818181818182
    },
    ...
    {
      "font-size": "110px",
      "baseline-offset": "92px",
      "baseline-height": "18px",
      "baseline-ratio": 0.16363636363636364
    }
  ]
}
```

### Google Fonts with Web Font Loader
**JS**
```javascript
WebFont.load({
  google: {
    families: ['Droid Sans']
  },
  fontactive: function(familyName) {
    var baseline = getBaseline(familyName);
  }
});
```
**Returns**
```json
{
  "font-family": "Droid Sans",
  "font-size-range": [
    11,
    110
  ],
  "baseline-ratio": 0.1661906238241618,
  "data": [
    {
      "font-size": "11px",
      "baseline-offset": "9px",
      "baseline-height": "2px",
      "baseline-ratio": 0.18181818181818182
    },
    ...
    {
      "font-size": "110px",
      "baseline-offset": 93,
      "baseline-height": 17,
      "baseline-ratio": 0.15454545454545454
    }
  ]
}
```

### Specific Font size
**JS**
```javascript
var baseline = getBaseline(null, [76]);
```
**Returns**
```json
{
  "font-family": "Apple SD Gothic Neo",
  "font-size-range": [
    76
  ],
  "baseline-ratio": 0.21052631578947367,
  "data": [
    {
      "font-size": "76px",
      "baseline-offset": 60,
      "baseline-height": 16,
      "baseline-ratio": 0.21052631578947367
    }
  ]
}
```

### Specific Element
**HTML**
```html
<p id="lead" style="font-family: 'Georgia';">abcdefg...</p>
```
**JS**
```javascript
var elem = document.getElementById('lead');
var baseline = getBaseline(null, null, elem);
```
**Returns**
```json
{
  "font-family": "Georgia",
  "font-size-range": [
    11,
    110
  ],
  "baseline-ratio": 0.16290896191698556,
  "data": [
    {
      "font-size": "11px",
      "baseline-offset": "9px",
      "baseline-height": "2px",
      "baseline-ratio": 0.18181818181818182
    },
    ...
    {
      "font-size": "110px",
      "baseline-offset": "93px",
      "baseline-height": "17px",
      "baseline-ratio": 0.15454545454545454
    }
  ]
}
```

## Browser Support
todo
[] 브라우저 서포트 체크
[] 브라우저 마다 값이 다른 것을 알려줌
[] 관련 포스트 링크

## Copyright and license

Code and documentation copyright 2017 designmeme. Code released under the [MIT License](LICENSE).