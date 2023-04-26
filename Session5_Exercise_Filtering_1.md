# Session 5 Exercise - 1
This is a reference of Code for Session 5 Exercise.

In this step we will apply the changes needed from the slides to create a Filtering.

### Add a search event
Add a search event in the FilterBar control and name it onSearch.

```xml
<filterbar:FilterBar search="onSearch">
```

### Assign an id to your Orders Table
Assign an id to your table and name it idOrders. 
```xml
<Table id="idOrders" items="{/Orders}">
```

### Reference the Filter and Filter Operator as modules
```js
sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/m/MessageToast",
    "zbootcamp/model/formatter",
    "sap/ui/model/Filter",
    "sap/ui/model/FilterOperator"
],
/**
 * @param {typeof sap.ui.core.mvc.Controller} Controller
 */
function (Controller, MessageToast, Formatter, Filter, FilterOperator) {
```

### Create onSearch function in the View1 controller
Get the value of the Order ID and use it to create a Filter. Get the table items using the table id and filter the table items.
```js
onSearch: function(){
    var oView = this.getView();
    var sValue = oView.byId("idOrder").getValue();
    var oFilter = new Filter ("OrderID", FilterOperator.EQ, sValue);

    oView.byId("idOrders").getBinding("items").filter(oFilter);
}

```
Test your application.

## Session 5 Exercise – Filtering– Multiple Values
In this step we will filter the table by Order ID and Customer ID. 

### Get the value of the Order ID and Customer ID
Go to your View1 controller and on the onSearch function get the value of the Order ID and Customer ID.

```js
var sOrderID = this.getView().byId("idOrder").getValue();
var sCustomerID = this.getView().byId("idCustomer").getValue();
```

### Get the table items using the table id
```js
var oBinding = this.getView().byId("idOrders").getBinding("items");
```

### Create a Filter with the Order ID and Customer ID values and use it to filter the table items.
```js
var aFilters = new Filter({
                    filters: [
                        new Filter({
                            path: "OrderID",
                            operator: FilterOperator.EQ,
                            value1: sOrderID
                        }),
                        new Filter({
                            path: "CustomerID",
                            operator: FilterOperator.EQ,
                            value1: sCustomerID
                        })
                    ],
                    and: true
                });
                oBinding.filter(aFilters);

```

Test your application.
