# Session 3 Exercises 
This is a reference of Code for Session 3 Exercise.

## Session 3 Exercise - Data Binding
In this exercise we will use the 3 types of Data Binding (Aggregation, Context, Property).

### Create JSON data
Create a new file `northwind.json` under `models` folder.
```json
{
	"Orders" : [
		{
			"OrderID": 10250,
			"CustomerID": "HANAR",
			"ShippedDate": "1996-07-12",
			"ShipCountry": "Brazil"
		},
		{
			"OrderID": 10251,
			"CustomerID": "VICTE",
			"ShippedDate": "1996-07-15",
			"ShipCountry": "France"
		},
		{
			"OrderID": 10252,
			"CustomerID": "SUPRD",
			"ShippedDate": "1996-07-11",
			"ShipCountry": "Belgium"
		},
		{
			"OrderID": 10253,
			"CustomerID": "HANAR",
			"ShippedDate": "1996-07-16",
			"ShipCountry": "Brazil"
		},
		{
			"OrderID": 10254,
			"CustomerID": "CHOPS",
			"ShippedDate": "1996-07-23",
			"ShipCountry": "Switzerland"
		},
		{
			"OrderID": 10255,
			"CustomerID": "RICSU",
			"ShippedDate": "1996-07-15",
			"ShipCountry": "Switzerland"
		}
	]
}

```

### Add JSON in manifest file
In your `manifest.json` add the northwind json under models after `i18n`.
```js
"models": {
  "i18n": {
    "type": "sap.ui.model.resource.ResourceModel",
    "settings": {
      "bundleName": "zbootcamp.i18n.i18n"
    }
  },
  "northwind": {
    "type": "sap.ui.model.json.JSONModel",
    "settings": {},
    "uri": "model/northwind.json",
    "preload": true
  }
},
```

### Use Property Binding in the Table Columns
In your northwind.json, add a new array Columns after Orders.
```json
"Columns" :[
		{
			"OrderID": "Order",
			"CustomerID": "Customer",
			"ShippedDate": "Shipped Date",
			"ShipCountry": "Shipped Country"
		}
	]
```

In the columns, bind the Column Labels in the Column text.
```xml
<columns>
	<Column id="idColumnOrder">
	    <Text id="idTextOrder" text="{northwind>/Columns/0/OrderID}" />
	</Column>
	<Column id="idColumnCustomer">
	    <Text id="idTextCustomer" text="{northwind>/Columns/0/CustomerID}" />
	</Column>
	<Column id="idColumnShipDate">
	    <Text id="idTextShipDate" text="{northwind>/Columns/0/ShippedDate}"/>
	</Column>
	<Column id="idColumnShipCountry">
	    <Text id="idTextShipCountry" text="{northwind>/Columns/0/ShipCountry}" />
	</Column>
</columns>

```

### Use Aggregation Binding in the Table  
In your `View1 xml`, add attribute items in your Table. The attribute `items` binds the children of our json model’s orders array to the Table. 
This by itself is not enough to display the orders, instead it sets the parent path for the binding of all contained list items and their descendants.
```xml
<Table id="idTableOrders" items="{northwind>/Orders}">
```

### Use Context Binding in the Table Row
In addition you need to declare a nested element.The nested items element in our case contains a `ColumnListItem`. This serves as a template for creating the individual rows.
```xml
<items>
    <ColumnListItem id="idColumnListItem">
        <cells>
            <ObjectIdentifier id="idOrderID" title="{northwind>OrderID}" />
            <Text id="idCustomerID" text="{northwind>CustomerID}" />
            <Text id="idShipDate" text="{northwind>ShippedDate}" />
            <Text id="idShipCountry" text="{northwind>ShipCountry}" />
        </cells>
    </ColumnListItem>
</items>
```

Test your application. 
