# Air Datepicker

# CDN



```html



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/air-datepicker/2.2.3/css/datepicker.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/air-datepicker/2.2.3/js/datepicker.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/air-datepicker/2.2.3/js/i18n/datepicker.en.js"></script>

</head>
<body>

<input type='text' class='datepicker-here' data-language='en' />

</body>
</html>






```

<p>disable specific date </p>

```html




<html>
<head>
    <link href="dist/css/datepicker.min.css" rel="stylesheet" type="text/css">

    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js" integrity="sha512-894YE6QWD5I59HgZOGReFYm4dnWc1Qt5NtvYSaNcOP+u1T9qYdvdihz0PPSiiqn/+/3e7Jo4EaG7TubfWGUrMQ==" crossorigin="anonymous"></script>
    <script src="dist/js/datepicker.min.js"></script>
    <!-- Include English language -->
    <script src="dist/js/i18n/datepicker.en.js"></script>
</head>
<body>

<input type="text"
       id="disabled-days"
       class="datepicker-here"
       data-language='en'
       />


<script>
    // Make Sunday and Saturday disabled
    var disabledDates = ['2021.10.4', '2021.10.17', '2021.10.20', '2021.10.23']

    $('#disabled-days').datepicker({
        language: 'en',
        onRenderCell: function(d, type) {
            if (type == 'day') {
                var disabled = false,
                    formatted = getFormattedDate(d);

                disabled = disabledDates.filter(function(date){
                    return date == formatted;
                }).length

                return {
                    disabled: disabled
                }
            }
        }
    })

    function getFormattedDate(date) {
        var year = date.getFullYear(),
            month = date.getMonth() + 1,
            date = date.getDate();

        return year + '.' + month + '.' + date;
    }
</script>

</body>

</html>


```

## change formate

```php

    $checkIn = date('Y-m-d', strtotime($request->checkin));
    $checkOut = date('Y-m-d', strtotime($request->checkout));

```


## Install

### bower
```
bower i --save air-datepicker
```
### npm
```
npm i --save air-datepicker
```

## Usage
```javascript
$('.my-datepicker').datepicker([options])
```

## Demo and docs
* [In English](http://t1m0n.name/air-datepicker/docs/)
* [In Russian](http://t1m0n.name/air-datepicker/docs/index-ru.html)

## Change log

### v2.2.3
* fixed min,max dates in decade mode

### v2.2.2
* fixed min,max dates handling

### v2.2.1
* changed RegExp for recognizing date parts
* changed jquery version dependency

### v2.2.0
* added `onlyTimepicker` option
* added `onShow` and `onHide` callbacks
* added `VERSION` field to plugin's prototype
* now for selecting same date in `range` mode, you should set `{toggleSelected: false}`
* fixed `dateFormat` method (fixed wrong month name in Hungarian language)
* fixed second call of `onRenderCallback`
* fixed `_getCell()` throwing exception
* new language:
    - `sk` thanks to [RobiNN1](https://github.com/RobiNN1)


### v2.1.0
* added possibility to select single date when `{range: true}`
* added support of 12 hours mode in `altFieldDateFormat`
* improved work with minDate and maxDate when `{timepicker: true}`
* fixed wrong class adding when `{range: true}`
* new languages:
    - `es` thanks to [MarioAraque](https://github.com/MarioAraque)
    - `cs` thanks to [liborm85](https://github.com/liborm85)
    - `hu` thanks to [gergo85](https://github.com/gergo85)
    - `fi` thanks to [joonaskaskisolaphz](https://github.com/joonaskaskisolaphz)
    - `pl` thanks to [xiio](https://github.com/xiio)
    - `fr` thanks to [nicooprat](https://github.com/nicooprat)

### v2.0.2
* fixed dates array in `onSelect` callback

### v2.0.1
* fixed version for npm

### v2.0.0
* added timepicker (see [docs](http://t1m0n.name/air-datepicker/docs#timepicker) for more info)
* added possibility to set `Date` in `todayButton`
* global variable `Datepicker` has been removed, now all placed in `$.fn.datepicker`
* improved `selectDate` method, now one can pass an array of dates to select
* added `npm` package
* fixed issue caused by `placeholder` on `readonly` inputs in IE
* fixed issue when `range` is true and first selected date is bigger than second
* added new languages:
    - `da`  thanks to [bjarnef](https://github.com/bjarnef)
    - `nl`  thanks to [JaZo](https://github.com/JaZo)
    - `pt`  thanks to [cmpscabral](https://github.com/cmpscabral)
    - `pt-BR`  thanks to [dowglaz](https://github.com/dowglaz)
    - `ro`  thanks to [tourniquet](https://github.com/tourniquet)

### v1.2.4
* fixed '$ is not defined' problem.

### v1.2.3
* fixed `dateFormat` method.
* fixed typo in Russian docs, add ids in docs headers.

### v1.2.2
* fixed typo in `monthsField`
* added German language (thanks to [Ichag](https://github.com/Ichag))

### v1.2.1
* tests added
* added Chinese language (thanks to [think2011](https://github.com/think2011))
* fixed if '0' is passed to `firstDay`
* fixed `showOtherYears` option
* fixed `onSelect` event, when `range` is true
* fixed case when `range` and `multipleDates` both set to true

### v1.2.0
* add `range` feature
* improve keyboard navigation (fixed two focused cells)

### v1.1.0
* add keyboard navigation
* add `classes` option to add custom classes
* add `altField` option
* bug fixes
