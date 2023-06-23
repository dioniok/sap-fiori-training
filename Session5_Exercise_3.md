## Session 5 - Exercise 3
This is a reference of Code for Session 5 Exercise.

## Session 5 Exercise – Post Request 
In this step we will create a post request to backend using **Create Order**.

### Add the MessageBox as module.
On your controller file add the MessageBox library and declare it as global variable

```js
sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/m/MessageToast",
    "zbootcamp/model/formatter",
    "sap/ui/model/Filter",
    "sap/ui/model/FilterOperator",
    "sap/ui/model/Sorter",
    "sap/m/MessageBox" //Add MessageBox
],
/**
 * @param {typeof sap.ui.core.mvc.Controller} Controller
 */
function (Controller, MessageToast, Formatter, Filter, FilterOperator, Sorter, MessageBox) { //Add MessageBox
```

### Create a new button for create
In your ``View1 xml``, add a new button for Create inside the OverflowToolbar of the table.

```xml
  <OverflowToolbar id="idHeaderToolbar">
    <Title id="idTitle" text="Orders (6)" />
    <ToolbarSpacer id="idHdrToolBarSpacer"/>
    <!--Create new button Add-->
    <Button id="idCreateBtn" press="onCreate" icon="sap-icon://add"/>
    <Button id="idSortBtn" press="onSort" icon="sap-icon://sort"/>
  </OverflowToolbar>
```

Create a new function ``onCreate``. Create the data and get the model and use method create to send a POST request to backend. 
```js
onCreate: function(){
    var data = {
        OrderID: 10448,
        CustomerID: "RICAR",
        ShipVia: 2
    };
    var odataModel = this.getView().getModel();
    odataModel.create("/Orders", data, {
        success: function(data, response){
            MessageBox.success("Data successfully created");
        },
        error: function(error){
            MessageBox.error("Error while creating the data");
        }
    });
}
```

Test your application. 
