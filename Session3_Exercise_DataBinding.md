# Session 3 Exercises 
This is a reference of Code for Session 3 Exercise.

## Session 3 Exercise - Data Binding
In this exercise we will use the 3 types of Data Binding (Aggregation, Context, Property).

### Create JSON data
Create a new file northwind.json under models folder.
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
In your manifest.json add the northwind json under models after i18n.
```js
"models": {
  "i18n": {
    "type": "sap.ui.model.resource.ResourceModel",
    "settings": {
      "bundleName": "project1.i18n.i18n"
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

### Use Aggregation Binding in the Table  
In your View1 xml, add attribute items in your Table. The attribute items binds the children of our json model’s orders array to the Table. 
This by itself is not enough to display the orders, instead it sets the parent path for the binding of all contained list items and their descendants.
```xml
<Table items="{northwind>/Orders}">
```

### Use Context Binding in the Table Row
In addition you need to declare a nested element.The nested items element in our case contains a ColumnListItem. This serves as a template for creating the individual rows.
```xml
<items>
    <ColumnListItem>
        <cells>
            <ObjectIdentifier title="{northwind>OrderID}" />
            <Text text="{northwind>CustomerID}" />
            <Text text="{northwind>ShippedDate}" />
            <Text text="{northwind>ShipCountry}" />
        </cells>
    </ColumnListItem>
</items>
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
    <Column>
        <Text text="{northwind>/Columns/0/OrderID}" />
    </Column>
    <Column>
        <Text text="{northwind>/Columns/0/CustomerID}" />
    </Column>
    <Column>
        <Text text="{northwind>/Columns/0/ShippedDate}"/>
    </Column>
    <Column>
        <Text text="{northwind>/Columns/0/ShipCountry}" />
    </Column>
</columns>

```

Test your application. 
