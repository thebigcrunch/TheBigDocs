# The Big Crunch SDK

Any space in The Big Crunch can be embedded into any webpage. The Big Crunch will keep the cell up to date on your website automatically.

# Embed a cell on your website

How to embed content from TheBigCrunch on the web.

1.  Find the space in The Big Crunch you want to embed
2.  In the bottom content bar, click the SHARE button
3.  Copy the HTML code from the Embed window
4.  Paste the code into your website

When the cell changes in The Big Crunch it will change on your website.

# Using a cell in your javascript code

Any cell in The Big Crunch can be extracted and used on your website using javascript. This is done using the TBC api.

## Install the TBC library

install with npm

`npm install tbc --save`

include in your HTML

`<script src="tbc.js"></script>`

### TBC API

`TBC.crunch(spaceId, changeCallback)`

* `spaceId` (String) The id of the space in The Big Crunch
* `changeCallback(value, cell)` (Function) A function that gets called whenever the cell changes

Creates a new connection to The Big Crunch and calls the `changeCallback` function with the cell value and details. Every time the cell changes the function is called again.

* `changeCallback(value, cell)`
  * `value` (String) The value of the cell depending on the type of the cell different values will be returned.
    * Scalar - the raw value in a string
    * Image - a fully qualified url for the image
    * Visualisation -
    * Layered Space - undefined
  * `cell` (Object)
    * `type` (String) type of the cell, can be compared to TBC.types
    * `value` (string) same as the first parameter `value`
    * `properties` (Object) a map of the properties for the cell. Includes font styling.
    * `layers` (Object) a map of the layers for the cell
    * `cellSize` (Object) the size of the merge of the cell (x, y)
