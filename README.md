# Accordion component

Accordions allow a number of sections on page to be collapsed, so that only
their headers are displaying. This can make it easier for users to quickly
scan for the section they are looking for.

Individual sections can be opened or closed by the user by clicking on the header.
This interactivity is made apparent through styling the header text (often blue),
and through the addition of an icon showing the current state (open or closed)
of the section.

In addition, a button at the top of the accordion makes it possible to open or close
all sections in a single action, which is useful if a user prefers to scan the content
of all sections.

This component includes the javascript for the show/hide functionality, as well as some
CSS and image icons. You can chose to apply your own styling by using the javascript only.

## Dependencies and backwards compatibility

The javascript does not require jQuery or any other frameworks. However it does require
some APIs not present in older browsers (notably older versions of Internet Explorer).

Where the browser doesn't support the required APIs, the javascript doesn’t alter the HTML,
allowing all the sections to be read normally. This is a form of Progressive Enhancement.

The accordion can be made to work in older browsers, as far back as Internet Explorer 8,
through the use of polyfills which add the required API functionality.

These aren’t included, but can be downloaded elsewhere:

* [addEventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#Compatibility) – polyfill available on the MDN website.
* [bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind#Polyfill) – polyfill available on the MDN website.
* [classList](https://github.com/eligrey/classList.js/blob/master/classList.js) – polyfill from `eligrey` on GitHub
* [textContent](https://developer.mozilla.org/en/docs/Web/API/Node/textContent#Polyfill_for_IE8) - polyfill from MDN.

## HTML structure

To make use of the accordion, you should add the following HTML classes to the sections on your page:


```html
<div class="accordion">

  <div class="accordion-section">

    <div class="accordion-section-header">
      <h2 class="heading-medium">Section title</h2>
    </div>
    <div class="accordion-section-body">
      <ul class="list"><li>Section content</li></ul>
    </div>

  </div>
  <div class="accordion-section">

    <div class="accordion-section-header">
      <h2 class="heading-medium">Section title</h2>
    </div>
    <div class="accordion-section-body">
      <ul class="list"><li>Section content</li></ul>
    </div>

  </div>
</div>
```

The javascript adds the following classes and elements, which are used for styling and accessibility:

```html
<div class="accordion">
  <div class="accordion-controls">
    <button class="accordion-expand-all" aria-expanded="false">Open all</button>
  </div>

  <div class="accordion-section" aria-expanded="true">

    <div class="accordion-section-header">
      <h2 class="heading-medium">Section title</h2>
    </div>
    <div class="accordion-section-body">
      <ul class="list"><li>Section content</li></ul>
    </div>

  </div>
  <div class="accordion-section" aria-expanded="false">

    <div class="accordion-section-header">
      <h2 class="heading-medium">Section title</h2>
    </div>
    <div class="accordion-section-body">
      <ul class="list"><li>Section content</li></ul>
    </div>

  </div>
</div>
```

Multiple accordions can be added per page, but this isn’t recommended.

## Initialising the accordions.

By default, the javascript just defines an `Accordion` function, and
doesn’t do anything else.

To set up an accordion, you just need to initialized a new `Accordion`
object with a reference to an element, eg:

```javascript
  new Accordion(document.getElementById('my-accordion'))
```

Or to automatically do this on page load for every element with an `accordion`
class you can do this:

```javascript

if (
  'addEventListener' in document &&
  document.querySelectorAll
  ) {

  document.addEventListener('DOMContentLoaded', function() {

    var accordions = document.querySelectorAll('.accordion')

    for (var i = accordions.length - 1; i >= 0; i--) {
      new Accordion(accordions[i])
    };

  })

}

```


## TODOs

There’s a few things that could be done to improve this code or add functionality:

* More accessibility research.
* Investigate whether a `<details>` could (and should) be used, using native
  browser functionality where it exists.
* Save state about which sections to the URL query string, and restore state on page load,
  so that you could send a link to someone showing particular sections open.
* Add a CSS pre-processor so that the icons could be include as data-urls, saving a network request.
* Make the component available as an npm module and/or a Ruby Gem.
* Add tests.


## Acknowledgements

This was developed by multiple people at the Government Digital Service and across Government.

## See also

* The BBC has an [accordion pattern](http://www.bbc.co.uk/gel/guidelines/accordion) in its GEL pattern.
* Discussion about the [accordion pattern](https://paper.dropbox.com/doc/Accordions-4lnTjyNru2mN1XXjA1Xf3) on GOV.UK Design Patterns.