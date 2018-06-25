# Big Crunch Formulas In JavaScript

This is the Early Access (alpha) documentation for authoring JavaScript formulas in The Big Crunch. It covers the JavaScript API, built-in functions list, and various examples for creating interesting formulas.

## Creating a Formula

JavaScript code formulas are created in The Big Crunch by selecting a cell and then either selecting the `f(x) Formula` button on the left hand side tool bar or pressing `SHIFT-=`. This changes the cell to a formula type and launches the code editor. You can enter your formula code in the main window and also create and manage your code's `inputs` (parameters) on this dialog.

<img src="https://user-images.githubusercontent.com/3023731/40693269-de966eb6-63f9-11e8-8530-65d061e7bc5a.png" style="width:400px">

Code can be any valid JavaScript (Node 7.2) with a few restrictions (below). The return value of your formula is simply the last `expression` in the formula.

## Return Values

The last `expression` in the code becomes the value of the cell. When you save your code, the formula is executed by the crunch and the result of the last expression is inserted into the cell. Numbers, strings, and arrays are all valid return types.

### Single Return Values

A formula with:

```javascript
42 + 42;
```

would make the value of the cell 84. You can also define and use functions to help you, for example:

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
// create an object
let r = {
  value: 66,
  properties: {
    content: {
      "font-weight": "bold"
    }
  }
};

r; // the object as the last expression
```

### Content Properties

The following properites are supported:

| Property                | Description                                                                                   |
| ----------------------- | --------------------------------------------------------------------------------------------- |
| content.alignment       | The font alignment - `center`, `left`, `right`                                                |
| content.font-family     | The font family - `Slabo`, `Indie Flower`, `Inconsolata`, `Macondo`, `Monoton`, `Roboto Slab` |
| content.font-multiplier | A relative size multiplier that is applied to the default font size.                          |
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

There are a number of things you cannot do in your code, such as network calls, file system access, `set_timeout` etc. These are in place for security reasons. You can use most built-in JavaScript but cannot require the NodeJS modules. 

The maximum execution time for a function is 20 seconds.

The value result of a formula must change for the cell to update. If only the properties of a cell change the styles will not update on the cell.

## Input Parameters

Inputs allow your code to relay on values from other cells in the crunch. All inputs created on your cell are considered mandatory. If they are not linked to a value, your code does not run and an error is thrown. To link up an input `Shift-Drag` a cell over the formula cell and drop it onto the desired input. When you hover, the list of inputs appear for you to select.

Once an input is linked it can be referenced in the formula code just by using the input name, like any declared variable.

### Named Inputs
Inputs are created with names in the formula editor's right hand pane. Valid names conform to the variable naming scheme in JavaScript.

### Unnamed Inputs
You can also create inputs that have no name. These are created when you `Shift-Drag` a cell onto the formula and drop it on `Add new input` panel. Unamed inputs can be referenced in the function using the `inputs[]` array variable in your code. The unnamed inputs appear in the array in the same order they are in the formula editor input pane.

### Array Input Parameters

Parameters are usually single values, but you can also select a range of cells and `Shift-Drag` them onto an input parameter. They are ordered by row first then column. All array inputs are 2-dimensional arrays (even if you only link a single row or column).

<img src="https://user-images.githubusercontent.com/3023731/40693086-d7ac3708-63f8-11e8-8cb3-30ac508f2a3e.png" style="width:200px">

The above range produces the array `[[1,4,7], [2,5,8], [3,6,9]]`

#### Merges

The top left cell of a merged area is where the value will appear in an array and all the other cells underneath the merge will have a `null` value.

<img src="https://user-images.githubusercontent.com/3023731/40693213-9ea7f3a6-63f9-11e8-9ea7-645dc1494e82.png" style="width:200px">

The above range produces an array `[[1,4,7],[null,null,8],[null,6, null]]`

<a name="functions"></a>
# Inbuilt functions
The Big Crunch has a number of built-in functions for you to use. These are accessed through the `TBC` library provided to your code.

## TBC.Math

`TBC.Math.sum(arrayToSum)`

* `arrayToSum` The values to sum in the array

Sums all the values in the array, skipping null values and non-integer values.

`TBC.Math.mult(arrayToMutliply)`

* `arrayToMutliply` The values to multiple in the array

Multiplies all the values in the array, skipping null values and non-integer values.

More built-in functions are on their way. Feel free to propose new ones.
