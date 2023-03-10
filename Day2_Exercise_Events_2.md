# Day 2 Exercises - 2
This is a reference of Code for Day 2 Exercise.

## Day 2 Exercise - Event Handlers
In this step we will create a MessageBox control and display a message when the Process Order button is clicked. 

### Attach an Event Handler
Add press event in the Button
```xml
<Button text="Process Order" type="Emphasized" press="onProcessOrder"/>
```

### Create Event Function
Go to View1 controller and replace the onInit function with the press event function onProcessOrder.
```js
sap.ui.define([
    "sap/ui/core/mvc/Controller"
],
/**
 * @param {typeof sap.ui.core.mvc.Controller} Controller
 */
function (Controller) {
    "use strict";

    return Controller.extend("project1.controller.View1", {
        onProcessOrder: function () {

        }
    });
});
```

### Add MessageBox
Add the sap.m.MessageBox control and add a message. 
```js
onProcessOrder: function () {
    sap.m.MessageBox.alert("Hello World!");
}
```

Test your application.
