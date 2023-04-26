# Session 5 Exercise - 2
This is a reference of Code for Session 5 Exercise.

## Session 5 Exercise – Sorting
In this step we will sort the orders in descending order once the sort button is pressed.

### Remove and replace the Table items path
```xml
<Table id="idOrders" items="{/Orders}">
```

### Create a Sort Button
Go to your View1 xml and add a sort button inside the OverflowToolbar.

```xml
<headerToolbar>
  <OverflowToolbar>
      <Title text="Orders (6)" />
      <ToolbarSpacer/>
      <Button press="onSort" icon="sap-icon://sort"/>
  </OverflowToolbar>
</headerToolbar>
```

### Reference Sorter
Go to your View1 controller and add Sorter as reference.

```js
sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/m/MessageBox",
    "project2/model/formatter",
    "sap/ui/model/Filter",
    "sap/ui/model/FilterOperator",
    "sap/ui/model/Sorter" //Add Sorter as Module
],
    /**
     * @param {typeof sap.ui.core.mvc.Controller} Controller
     */
    function (Controller, MessageBox, Formatter, Filter, FilterOperator, Sorter) { //Add Sorter

```
### Add a press event and name it onSort
Create a Sorter with the path OrderID and set descending property to true. Get the table items using the table id and sort the table items. 

```js
onSort: function () {
    var oSorter = new Sorter({
        path: "OrderID",
        descending: true
    });
    this.getView().byId("idOrders").getBinding("items").sort(oSorter);
}

```

Test your application.
