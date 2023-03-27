### Day 4 Exercise - 1
This is a reference of Code for Day 4 Exercise.

## Day 4 Exercise – Odata Model Binding
In this exercise we will use the OData Model Northwind to bind in our table. 

# Retrieve data from Northwind service

Go to your View1 XML and remove all the northwind> prefixes in our bindings. Our OData Model is the default model, it means we do not need any prefixed model names when binding unlike what we did with the JSON Model.
```xml
<ColumnListItem>
  <cells>
    <ObjectIdentifier title="{OrderID}" />
    <Text text="{CustomerID}" />
    <Text text="{ShippedDate}" />
    <Text text="{ShipCountry}" />
  </cells>
</ColumnListItem>
```


Test your application. 
