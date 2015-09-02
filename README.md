Webcomponent for slickgrid. For slickgrid-element to work, a small change needs to be made to slick.grid.js. The required change, as of slickgrid 2.1.0 is:

`Change:   while ((elem = elem.parentNode) != document.body && elem != null) {`
`To:       while ((elem = elem.parentNode) != document.body && elem != null && elem.parentNode.toString() != "[object ShadowRoot]") {`
and
`Change:   while ((elem = elem.parentNode) != document.body) {`
`To:       while ((elem = elem.parentNode) != document.body && elem.toString() != "[object ShadowRoot]") {`

I.e., Including check that we aren't on ShadowRoot. The changed file should be called slick.grid.polymer.js, and be in the slickgrid directory. An example for 2.1.0 is given in this repo.

This repo also includes the cellexternalcopymanager from https://github.com/Celebio/SlickGrid. Slickgrid needs to be installed to use this component.
