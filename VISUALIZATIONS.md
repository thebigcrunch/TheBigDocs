# Big Crunch Visualization Authoring

## Introduction

Visualisations in The Big Crunch are a powerful way to visualise data and create apps. A visualisation is a HTML / CSS and javascript file that is run in The Big Crunch universe. Visualisations can be embedded like any other cell.

## Example

```html
<html>
    <head>
        <!-- Include the SDK -->
        <script src="/tbc_sdk.js"></script>
    </head>
    <body>
        <h1>This is a visualisation example</h1>
        <p>The inputs are...</p>
        <!-- a place to put our inputs -->
        <p id="inputs"></p>
        <script>
            // This function will be called every time an input changes
            function onChange(inputs) {
                document.getElementById('inputs').innerHTML = JSON.stringify(inputs);
                // Your code goes here....
            }

            // Setup the change event
            TBC.vizzy({onChange: onChange});
        </script>
    </body>
</html>
```

## API

`TBC.vizzy({onChange, onConfig})`

- `onChange` (function(inputs))
  - `inputs` An object that represents all the inputs for the visualisation cell. If an input is named it can be addressed by it's name `inputs.param`. It can also be address using the array on the inputs object eg. `inputs[0]`. Nameless parameters are in the array but can't be addressed directly.
- `onConfig` (function(configuration))

## Restrictions

To prevent cross site scripting attacks (XSS) visualisations are restricted from performing some actions. Visualisations run in a HTML 5 sandbox with the `allow-same-origin allow-scripts` flags additionally all visualisations are served from the `rur.bigcrunch.io` domain. [Iframe sandbox reference](https://www.w3schools.com/tags/att_iframe_sandbox.asp)
