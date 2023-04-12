# Day 5 Exercise - 1
This is a reference of Code for Day 5 Exercise.

## Day 5 Exercise – Filtering– Multiple Values
In this step we will filter the table by Order ID and Customer ID. 

###Get the value of the Order ID and Customer ID.
Go to your View1 controller and on the onSearch function get the value of the Order ID and Customer ID.

```js
var sOrderID = this.getView().byId("idOrder").getValue();
var sCustomerID = this.getView().byId("idCustomer").getValue();
```

###Get the table items using the table id.
```js
var oBinding = this.getView().byId("idOrders").getBinding("items");
```

###Create a Filter with the Order ID and Customer ID values and use it to filter the table items.
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
