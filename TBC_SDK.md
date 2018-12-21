# The Big Crunch SDK

Any cell in The Big Crunch can be embedded into any webpage. The Big Crunch will keep that cell up to date on your website automatically. So any chances in the grid to the space, automatically and in real time get propagated to all embedded views of that space.

There are a number of ways that cell an be embeded which are described below.

# Embedding a cell on your website as an `iframe`.

How to embed content from TheBigCrunch on the web.

1.  Find the cell in The Big Crunch you want to embed
2.  In the bottom content bar, click the `EMBED` button, and choose the `Easy` tab
3.  Copy the HTML code from the embed window
4.  Paste the code into your website

When the cell changes in The Big Crunch it will change on your website.

# Using cell content in your javascript code

Any cell in The Big Crunch can be extracted and sent to your website using JavaScript. This is done using the crunch SDK, `TBC.js`. When the cell changes in the grid, that change will propagate to your JavaScript code and invoke a callback.

## Using the `TBC.js` SDK library

First, include the SDK in your HTML

`<script src="https://rur.bigcrunch.io/tbc.js"></script>`

Or copy the sample code from the `Advanced` embed tab

<img style="width: 400px" src="https://user-images.githubusercontent.com/3023731/50318820-af015e80-0517-11e9-8c54-112b91274edb.png"/>

### TBC API
To register for changes to a cell call the `crunch` API

`TBC.crunch(spaceId, changeCallback)`

- `spaceId` (String) The id of the space in The Big Crunch
- `changeCallback(value, cell)` (Function) A function that gets called whenever the cell changes with the new value

This creates a new connection (websocket) to The Big Crunch and calls the `changeCallback()` function with the cell value and details on start up. Every time the cell value (not attributes!) changes the function is called again.

#### Cell Object
The callback receives a number properties about the cell, along with the value, depending on the type of the value. This is described below:

- `changeCallback(value, cell)`
  - `value` (String) The value of the cell depending on the type of the cell different values will be returned.
    - Scalar - the raw value in a string
    - Image - a fully qualified url for the image
    - Visualisation - null
  - `cell` (Object)
    - `value` (String) same as the first parameter `value`
    - `properties` (Object) a map of the properties for the cell. Includes font styling.
    - `layers` (Object) a map of the layers for the cell (for infographics only)
    - `cellSize` (Object) the size of the merge of the cell (x, y)z
    - `contentType` the type of the content, similar to a mime type. The currently supported types are
      - `text/text`
      - `video/youtube`
      - `image/png`
      - `image/gif`

