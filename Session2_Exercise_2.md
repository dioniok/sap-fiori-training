# Session 2 Exercises - 2
This is a reference of Code for Session 2 Exercise.

## Session 2 Exercise - Event Handlers
In this step we will create a MessageBox control and display a message when the Process Order button is clicked. 

### How to Format Code
You may use `Shift + Alt + F` to format your code in your JS and XML files. 

### Attach an Event Handler
Add a `press` event in the `Process Order Button`.
```xml
<Button id="idProcessBtn" text="Process Order" type="Emphasized" />
```

### Create Event Function
Go to `View1.controller.js` and a new function `onProcessOrder`.
```js
sap.ui.define([
    "sap/ui/core/mvc/Controller"
],
/**
 * @param {typeof sap.ui.core.mvc.Controller} Controller
 */
function (Controller) {
    "use strict";

    return Controller.extend("zbootcamp.controller.View1", {
        onInit: function () {

        }, 
        
        onProcessOrder: function () {

        }
    });
});
```

### Add MessageBox
Add the `sap.m.MessageBox` control and add a message. 
```js
onProcessOrder: function () {
    sap.m.MessageBox.alert("Hello World!");
}
```

Test your application.
