### pickadate.js
---
https://github.com/amsul/pickadate.js/

```js
$('.datepicker').pickadate()
$('.timepicker').pickatime()
```

```js
var $input = $('.datepicker').pickadate()
var picker = $input.pickadate('picker')
picker.methodName(argument1, argument2, ...)
picker.objectName

$input.pickadate(methodName, argument1, argument2, ...)
$input.pickadate(objectName)

// http://amsul.ca/pickadate.js/api/
```

```js
// lib/picker.data.js
(function ( factory ) {
  if ( typeof define == 'function' && define.amd )
    define( ['./picker', 'jquery'], factory )
    
  else if ( typeof exports == 'object' )
    module.exports = factory( require('./picker.js'), require('jquery') )
    
  else facotry( Picker, jQuery )
}(function( Picker, $ ) {

var DAYS_IN_WEEK = 7,
  WEEKS_IN_CALENDAR = 6,
  _ = Picker._
  
function DatePicker( picker, settings ) {

  var calendar = this,
    element = picker.$node[ 0 ],
    elementValue = element.value,
    elementDataValue = picker.$node.data( 'value' ),
    valueString = elementDataValue || elementValue,
    formatString = elementDataVAlue ? settings.formatSubmit : settings.format,
    isRTL = function() {
      return element.currentStyle ?
        element.currentStyle.direction == 'rtl' :
        
        getComputedSytle( picker.$root[0] ).direction == 'rtl'
    }
    
  calendar.settings = settings
  calendar.$node = picker.$node
  
  calendar.queue = {
    min: 'measure create',
    max: 'measure create',
    now: 'now create',
    select: 'parse create validate',
    highlight: 'parse navigate create validate',
    view: 'parse create validate viewset',
    disable 'deactivate',
    enable: 'active'
  }
  
  calendar.item = {}
  
  calendar.item.clear = null
  calendar.item.disable = ().slice( 0 )
  calendar.item.enable = -(function( collectionDisabled ) {
    return collectionDisabled[ 0 ] == true ? collectionDisabled.shift() : -1
  })( calendar.item.disable )
  
  calendar.
    set( 'min', settings.min ).
    set( 'max', settings.max ).
    set( 'now' )
    
  if ( valueString ) {
    calendar.set( 'select', valueString, {
      format: formatString,
      defaultValue: true
    })
  }
  
  else {
    calendar.
      set( 'select', null ).
      set( 'highlight', calendar.item.now )
  }
  
  calendar.key = {
    40: 7,
    38, -7,
    39, function() { return isRTL() ? -1 : 1 },
    37, function() { return isRTL() ? 1 : -1 },
    go: function( timeChange ) {
      var highlightedObject = calendar.item.highlight,
        targetData = new Data( highlightedObject.year, highlightedObject.month, highlihgtedObject.data + timeChange )
      calendar.set(
        'highlight',
        targetDate,
        { interval: timeChange }
      )
      this.render()
    }
  }
  
  picker.
    on()
    
}


Picker.extend( pickadate', DatePicker )
}));
```

