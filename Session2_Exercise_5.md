# Session 2 Exercises - 5
This is a reference of Code for Session 2 Exercise.

## Session 2 Exercise - Modules
In this step, we will add the MessageBox as a module.

### How to Format Code
You may use `Shift + Alt + F` to format your code in your JS and XML files. 

### Add module
Reference the target module on your controller. Use the callback function to reference the library/module. Show  message using the  built-in module.
```js
sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/m/MessageBox" //Reference MessageBox
],
/**
 * @param {typeof sap.ui.core.mvc.Controller} Controller
 */
function (Controller, MessageBox) {//Add MessageBox in callback function
    "use strict";

    return Controller.extend("zbootcamp.controller.View1", {
        onProcessOrder: function () {
            var oOrder = this.getView().byId("idOrder");
            var oCustomer = this.getView().byId("idCustomer");

            this.fnValidate(oOrder, oCustomer);
        },

        fnValidate: function(oOrder, oCustomer){
            if(oOrder.getValue() !== "" && oCustomer.getValue() !== ""){
                oOrder.setValueState("None");
                oCustomer.setValueState("None");
                //Use MessageBox module
                MessageBox.success("Order " + oOrder.getValue() + " has been processed for Customer " + oCustomer.getValue() + " sucessfully!" );
            } else {
                oOrder.setValueState("Error");
                oCustomer.setValueState("Error");
            }
        }
    });
});
```

Test your application. 
