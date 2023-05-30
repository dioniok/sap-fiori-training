# Session 2 Exercises - 4
This is a reference of Code for Session 2 Exercise.

## Session 2 Exercise - Simple Validation
In this step, we will replace the message in the MessageBox with the Order ID and Customer ID values entered. 

### How to Format Code
You may use `Shift + Alt + F` to format your code in your JS and XML files. 

### Get fields by ID
Go to your `View1.controller.js`, get the input fields from the view using its ID’s.
```js
onProcessOrder: function () {
    var oOrder = this.getView().byId("idOrder");
    var oCustomer = this.getView().byId("idCustomer");

    sap.m.MessageBox.alert("Hello World!");
}
```

### Get the values 
Change the type of the `MessageBox` to `sucess` and get the value of the fields and display in the MessageBox. 
```js
onProcessOrder: function () {
    var oOrder = this.getView().byId("idOrder");
    var oCustomer = this.getView().byId("idCustomer");

    sap.m.MessageBox.success("Order " + oOrder.getValue() + " has been processed for Customer " + oCustomer.getValue() + " sucessfully!" );
}
```

Test your application.

### Create a Validation
In this step we will create a validation when the Order ID and Customer ID is blank.

In the `View1.controller.js`, create a custom function `fnValidate` and create an if else statement that checks if the input field is not blank.
```js
fnValidate: function(oOrder, oCustomer){
    if(oOrder.getValue() !== "" && oCustomer.getValue() !== ""){
        oOrder.setValueState("None");
        oCustomer.setValueState("None");
        sap.m.MessageBox.success("Order " + oOrder.getValue() + " has been processed for Customer " + oCustomer.getValue() + " sucessfully!" );
    } else {
        oOrder.setValueState("Error");
        oCustomer.setValueState("Error");
    }
}
```

Replace the code inside the press event function `onProcessOrder` and call the custom function `fnValidate` passing the `Order ID` and `Customer ID` as parameters.
```js
onProcessOrder: function () {
    var oOrder = this.getView().byId("idOrder");
    var oCustomer = this.getView().byId("idCustomer");

    this.fnValidate(oOrder, oCustomer);
},
```

Test your application. 
