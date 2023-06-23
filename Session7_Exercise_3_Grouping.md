# Session 7 Exercise - 3
This is a reference of Code for Session 7 Exercise.

## Session 7 Exercise – Grouping
In this step we will group the orders by `ShipCountry`.

### Create a Group Button
Go to your `View1.view.xml` and add a group button inside the `OverflowToolbar`.

```xml
 <headerToolbar>
  <OverflowToolbar id="idHeaderToolbar">
    <Title id="idTitle" text="Orders (6)" />
    <ToolbarSpacer id="idHdrToolBarSpacer"/>
    <Button id="idSortBtn" press="onSort" icon="sap-icon://sort"/>
    <Button id="idGroupBtn" press="onGroup" icon="sap-icon://group-2"/>
  </OverflowToolbar>
 </headerToolbar>
```

### Add a press event and name it onGroup
Create a Sorter with the path ShipCountry and set group property to true. Get the table items using the table id and sort the table items. 

```js
onGroup: function() {
    var oSorter = new Sorter({
      path: "ShipCountry",
      group: true
    });
    this.getView().byId("idOrders").getBinding("items").sort(oSorter);
},

```

Test your application.
