# Session 2 Exercises - 3
This is a reference of Code for Session 2 Exercise.

## Session 2 Exercise - Simple Validation
In this step, we will replace the message in the MessageBox with the Order ID and Customer ID values entered. 

### Identify Objects in View
To create a simple validation, we must identify the objects from our view. To identify objects, we can assign IDs to each element and use them on the controller.
```xml
<filterbar:FilterBar>
    <filterbar:filterGroupItems>
        <filterbar:FilterGroupItem name="order" groupName="a" visibleInFilterBar="true" label="Order ID">
            <filterbar:control>
                <Input id="idOrder"/>
            </filterbar:control>
        </filterbar:FilterGroupItem>
        <filterbar:FilterGroupItem name="customer" groupName="a" visibleInFilterBar="true" label="Customer ID">
            <filterbar:control>
                <Input id="idCustomer"/>
            </filterbar:control>
        </filterbar:FilterGroupItem>
    </filterbar:filterGroupItems>
</filterbar:FilterBar>
```

### Get fields by ID
In the View1 controller, get the input fields from the view using its ID’s.
```js
onProcessOrder: function () {
    var oOrder = this.getView().byId("idOrder");
    var oCustomer = this.getView().byId("idCustomer");

    sap.m.MessageBox.alert("Hello World!");
}
```

### Get the values 
Change the type of the MessageBox to sucess and get the value of the fields and display in the MessageBox. 
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

In the View1 controller, create a custom function fnValidate and create an if else statement that checks if the input field is not blank.
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

Replace the code inside the press event function onProcessOrder and call the custom function fnValidate passing the Order ID and Customer ID as parameters.
```js
onProcessOrder: function () {
    var oOrder = this.getView().byId("idOrder");
    var oCustomer = this.getView().byId("idCustomer");

    this.fnValidate(oOrder, oCustomer);
},
```

Test your application. 
