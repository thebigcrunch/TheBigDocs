# Big Crunch Formulas In JavaScript

This is the Alpha documentation for authoring JavaScript formulas in The Big Crunch. It covers the JavaScript API, built-in functions list, and various examples for creating interesting formulas.

## Creating a Formula

Javascript code formulas are created in The Big Crunch by selecting a cell and then pressing `SHIFT-=`. This launches the code editor. You can enter your code here, and create and manage your code's `Parameters` on this dialog.

<img src="https://user-images.githubusercontent.com/3023731/40693269-de966eb6-63f9-11e8-8530-65d061e7bc5a.png" style="width:400px">

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

<img src="https://user-images.githubusercontent.com/3023731/40693313-17709310-63fa-11e8-8356-417a11b0b5c2.png" style="width:300px"/>

To change a content property you need to a return an `Object` from your code with the properties as an attribute. The cell result in this case goes in the `value` property. This code would set the value of the cell to 66 and make it bold:

```javascript
let r = {
  value: 66,
  properties: {
    content: {
      "font-weight": "bold"
    }
  }
};
```

### Content Properties

The following properites are supported:

| Property                | Description                                                                                   |
| ----------------------- | --------------------------------------------------------------------------------------------- |
| content.alignment       | The font alignment - `center`, `left`, `right`                                                |
| content.font-family     | The font family - `Slabo`, `Indie Flower`, `Inconsolata`, `Macondo`, `Monoton`, `Roboto Slab` |
| content.font-multiplier | Similar to font-size, but scales at different zoom levels in The Big Crunch, default is 1     |
| content.color           | The font color in a hex string #000000                                                        |
| content.content         | The fit style for the cell - `fit`, `wrap`, `truncate`                                        |

#### Example

``` javascript
a = {
    value: 'The Big Docs!',
    properties: {
        content: {
            alignment: 'right',
            color: '#123456',
            "font-multiplier": .3,
            "font-family": 'Indie Flower'
        }    
    }
}	

a
```

The code above produces the following cell

<img src="https://user-images.githubusercontent.com/3023731/40694153-7ddbd278-63fe-11e8-8765-ba68c09daca0.png"  />


### Code Restrictions

There are a number of things you cannot do in your code, such as network calls, file system access, `set_timeout` etc. These are in place for security reasons.

The maximum execution time for a function is 20 seconds.

The value result of a formula must change for the cell to update. If only the properties of a cell change the styles will not update on the cell.

## Parameters

Parameters defined for your cell are considered mandatory. If they are not linked to a value, your code does not run.

### Named Parameters

Named parameters are created in the formula editor in the right hand pane. To link up a parameter `SHIFT-drag` it over the formula cell and link it to the parameter.

Once a parameter is linked it can be referenced in the function using the name.

### Unnamed Parameters

To create a unnamed parameter `SHIFT-drag` a cell onto the formula and drop it on `Add new input`. Unamed parameters can be referenced in the function using the `inputs` array. The unnamed parameters appear in the array in the same order they are in the formula editor parameters pane.

### Array Parameters

Parameters are usually single values, but you can also select a range of cells and `SHIFT-Drag` them onto a parameter. They are ordered by row first then column.

<img src="https://user-images.githubusercontent.com/3023731/40693086-d7ac3708-63f8-11e8-8cb3-30ac508f2a3e.png" style="width:200px">

The above range produces an array `[[1,4,7], [2,5,8], [3,6,9]]`

#### Merges

The top left of a merge is where the value will appear in an array and the other merged cells will have a null value.

<img src="https://user-images.githubusercontent.com/3023731/40693213-9ea7f3a6-63f9-11e8-9ea7-645dc1494e82.png" style="width:200px">

The above range produces an array `[[1,4,7],[null,null,8],[null,6, null]]`

# Inbuilt functions

## TBC.Math

`TBC.Math.sum(arrayToSum)`

* `arrayToSum` The values to sum in the array

Sums all the values in the array, skipping null values and non-integer values.

`TBC.Math.mult(arrayToMutliply)`

* `arrayToMutliply` The values to multiple in the array

Multiplies all the values in the array, skipping null values and non-integer values.
