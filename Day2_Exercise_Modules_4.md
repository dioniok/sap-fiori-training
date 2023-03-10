# Day 2 Exercises - 4
This is a reference of Code for Day 2 Exercise.

## Day 2 Exercise - Modules
In this step, we will add the MessageBox as a module.

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

    return Controller.extend("project1.controller.View1", {
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
