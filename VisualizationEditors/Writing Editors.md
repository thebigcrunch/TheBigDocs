# Writing visualization editors

## What is a visualization editor?

The Grid view of The Big Crunch is very powerful, but doesn't work for everyone that's why we've created web editors for visualizations. There is a standard set of features that you can take advantage of to make easy web editors for your visualizations. The editor appears next to your visualization in web view when you're logged in and you have write permission to the space the visualisation is in.

![Webview Editor screenshot](https://user-images.githubusercontent.com/3023731/60233577-36bf8f80-98e4-11e9-9059-024dac051ba7.png "Web view editor screenshot")

## How to edit the visualization editor

The editor is defined in a JSON format. The JSON schema is next to this document. To edit the JSON it's in the HTML editor in the Gird view as a second tab.

![Editor tab to change the JSON](https://user-images.githubusercontent.com/3023731/60234821-ff071680-98e8-11e9-95e9-ff160dd9c11b.png "Editor Tab to change the JSON")

## Tabs

Tabs make contain controls to edit cells. Only a title field is required for them

```json
{
    "title": "Data",
    "content": "...."
}
```

![](https://user-images.githubusercontent.com/3023731/60233674-a766ac00-98e4-11e9-8fd1-6c2ca4d1629b.png)

## Content

The content section contains the controls to edit parameters in your visualisation. List below are the different types of inputs the content type can contain. Every control added must be associated with a parameter name from a visualisation. This is in the property parameterName

```json
{
    "parameterName": "NameOfAInputInYourVisualisation",
    "control": "..."
}
```

### Tables

Tables are a main control that is used because they lend themselves well to editing grid content. Rows appear in the table only if there is a value in every column.

Valid controls in a table are

    Text
    Number
    ColourPicker
    Image
    Slider
    Label

Other table settings

`showWhenFilled` - if this is set to true and the column has a value the column is shown in the editor, false by default

`addRow` - if the user can add rows to the table or not. true by default

Example Table:

```json
{
    "content": {
        "parameterName": "data",
        "control": "Table",
        "addRow": true,
        "columns": [
            {
                "label": "Label",
                "control": "Text",
                "showWhenFilled": true
            },
            {
                "label": "Series 1",
                "control": "Number"
            },
            {
                "label": "Series 2",
                "control": "Number"
            },
            {
                "label": "Series 3",
                "control": "Number"
            }
        ]
    }
}
```

![](https://user-images.githubusercontent.com/3023731/60233842-6de27080-98e5-11e9-8e1e-2e6339a34748.png)

### Other Controls

Outside of tables you can modify individual cells

valid controls are:
Text
Number
ColourPicker
Slider
InlineSelector
TextArea
Selector
Image
Table

Section example

```json
"title": "Configuration",
            "content": [
                {
                    "parameterName": "palette",
                    "control": "Selector",
                    "options": ["normal", "mature", "colorful"],
                    "label": "Color - Palette"
                },
                {
                    "parameterName": "seriesType",
                    "control": "Selector",
                    "options": ["line", "bar", "area"],
                    "label": "Series 1 Type"
                },
                {
                    "parameterName": "seriesType2",
                    "control": "Selector",
                    "options": ["line", "bar", "area"],
                    "label": "Series 2 Type"
                },
                {
                    "parameterName": "seriesType3",
                    "control": "Selector",
                    "options": ["line", "bar", "area"],
                    "label": "Series 3 Type"
                },
                {
                    "parameterName": "seriesName",
                    "control": "Text",
                    "label": "Series 1 Name"
                },
                {
                    "parameterName": "seriesName2",
                    "control": "Text",
                    "label": "Series 2 Name"
                },
                {
                    "parameterName": "seriesName3",
                    "control": "Text",
                    "label": "Series 3 Name"
                }
```

![](https://user-images.githubusercontent.com/3023731/60234454-a2572c00-98e7-11e9-92c3-9e4bde02b421.png)

#### Text

A simple text box with a label

```json
{
    "parameterName": "seriesName",
    "control": "Text",
    "label": "Series 1 Name"
},
```

#### Number

A simple text box that only accepts numbers

```json
{
    "parameterName": "myNumber",
    "control": "Text",
    "label": "Enter your number"
},
```

#### Colour Picker

Produces a hex code colour eg. `#FFFFFF`

```json

{
    "parameterName": "myColor",
    "control": "Colour",
    "label": "Enter your colour"
},
```

#### Slider

The slider has a few options

`max` - the maximum value it can go up to

`min` - the minimum value it can go down to

`step`- how much each movement adds or subtracts to the number

```json

{
    "parameterName": "mySlider",
    "control": "Slider",
    "label": "some slider",
    "max": 100,
    "min": 10,
    "step": 5
},
```

#### InlineSelector

```json
{
    "parameterName": "singleSelect",
    "control": "InlineSelector",
    "options": ["Option A", "Option B", "Option C"],
    "label": "Inline Selector"
},
```

#### TextArea

```json
{
    "parameterName": "myText",
    "control": "TextArea",
    "label": "Text Area input"
},
```

#### Selector

Produces a drop down

```json
{
    "parameterName": "palette",
    "control": "Selector",
    "options": ["normal", "mature", "colorful"],
    "label": "Color - Palette"
}
```

# Future Developments

We're looking to add more controls to the editor and we'd love to hear what you would like to see. Please create a Github issue with the control you would like.
