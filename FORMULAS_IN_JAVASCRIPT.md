# Big Crunch Formulas In JavaScript

This is the Alpha documentation for authoring JavaScript formulas in TheBigCrunch. It covers the JavaScript API, built-in functions, and examples for creating formulas in The Big Crunch.

## Creating a Formula

Javascript code formulas are created in The Big Crunch by selecting a cell and then pressing `SHIFT-=`. This launches the code editor. You can enter your code here, and create and manage your code's `Parameters` on this dialog.

[SCREEN SHOT HERE]

Code can be any valid JavaScript (with a few restrictions). The return value of your formula is simply the last `expression` in the formula.

## Return Values

The last `expression` in the code becomes the value of the cell. When you save your code, the formula is executed by TheBigCrunch and the result of the expression is inserted into the cell. Numbers, strings, arrays, etc are all valid return types.

### Single Return Values

So a formula with just:

```javascript
1 + 1;
```

would make the value of the cell 2. You can also define and use functions to help you, for example:

```javascript
function addSix(value) {
  return value + 6;
}

addSix(5);
```

would result in `11` as the value of the cell.

### Changing Cell Properties

You can also change the cell content properties of the cell in your code. The properties are the cells styling attributes seen in the right-hand side slider, for example `font-:

[SCREEN SHOT HERE]

To change a content property you need to a return an `Object` from your code with the properties as an attribute. The cell result in this case goes in the `result` property. This code would set the value of the cell to 66 and make it bold:

```javascript
let r = {
  result: 66,
  properties: {
    content: {
      "font-weight": "bold"
    }
  }
};
```

### Content Properties

The following properites are supported:

[list the properties here in a table]

### Code Restrictions

There are a number of things you cannot do in your code, such as network calls, file system access, `set_timeout` etc. These are in place for security reasons.

## Parameters

Parameters defined for your cell are considered mandatory. If they are not linked to a value, your code does not get called.

### Named Parameters

### Unnamed Parameters

### Array Parameters

Parameters are usually single values, but you can also select a range of cells and `SHIFT-Drag` them onto a parameter.

<a id="libfunc"/>
# Library Functions

## Array

## Matrix

# TODO

Things to add to this doc

* 20 second execution time
*
