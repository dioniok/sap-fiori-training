# Session 4 Exercise - 1
This is a reference of Code for Session 4 Exercise.

## Session 4 Exercise – Odata Model Binding
In this exercise we will copy the codes from the previous project into the newly created project and use the OData Model Northwind to bind in our table. 

### Copy the codes from previous project to the new project

Copy your northwind.json file from the previous project and add it to your models folder in the new project. 
```js
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
	],
	"Columns" :[
		{
			"OrderID": "Order",
			"CustomerID": "Customer",
			"ShippedDate": "Shipped Date",
			"ShipCountry": "Shipped Country"
		}
	]
}
```

Go to your ``manifest.json`` file, under models section and add the northwind json model.
```js
"models": {
      "i18n": {
        "type": "sap.ui.model.resource.ResourceModel",
        "settings": {
          "bundleName": "zbootcamp.i18n.i18n"
        }
      },
      "": {
        "dataSource": "mainService",
        "preload": true,
        "settings": {}
      },
      "northwind": {
        "type": "sap.ui.model.json.JSONModel",
        "settings": {},
        "uri": "model/northwind.json",
        "preload": true
      }
    },

```
Go to your ``View1.view.xml`` and replace the code.

```xml
<mvc:View controllerName="zbootcamp.controller.View1" xmlns:mvc="sap.ui.core.mvc" displayBlock="true" xmlns="sap.m" xmlns:filterbar="sap.ui.comp.filterbar">
    <Page id="page" title="{i18n>title}">
        <content>
            <filterbar:FilterBar>
                <filterbar:filterGroupItems>
                    <filterbar:FilterGroupItem name="order" groupName="a" visibleInFilterBar="true" label="Order ID">
                        <filterbar:control>
                            <Input id="idOrder" value="{northwind>/Orders/0/OrderID}"/>
                        </filterbar:control>
                    </filterbar:FilterGroupItem>
                    <filterbar:FilterGroupItem name="customer" groupName="a" visibleInFilterBar="true" label="Customer ID">
                        <filterbar:control>
                            <Input id="idCustomer" value="{northwind>/Orders/0/CustomerID}"/>
                        </filterbar:control>
                    </filterbar:FilterGroupItem>
                </filterbar:filterGroupItems>
            </filterbar:FilterBar>
            <Table items="{northwind>/Orders}">
            <headerToolbar>
                <OverflowToolbar>
                    <Title text="Orders (6)" />
                </OverflowToolbar>
            </headerToolbar>
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
            </Table>
        </content>
        <footer>
            <OverflowToolbar>
                <content>
                    <ToolbarSpacer />
                    <Button text="Process Order" type="Emphasized" press="onProcessOrder"/>
                </content>
            </OverflowToolbar>
        </footer>
    </Page>
</mvc:View>
```

Go to your View1.controller.js and replace the code.
```js

sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/m/MessageToast"
],
/**
 * @param {typeof sap.ui.core.mvc.Controller} Controller
 */
function (Controller, MessageToast) {
    "use strict";

    return Controller.extend("zbootcamp.controller.View1", {
        onProcessOrder: function () {
            var oOrder = this.getView().byId("idOrder");
            var oCustomer = this.getView().byId("idCustomer");

            this.fnValidate(oOrder, oCustomer);
        },

        fnValidate: function(oOrder, oCustomer){
            if(oOrder.getValue() !== "" && oCustomer.getValue() !== ""){
                oOrder.setValueState("None");
                oCustomer.setValueState("None");
                
                MessageToast.show("Order " + oOrder.getValue() + " has been processed for Customer " + oCustomer.getValue() + " sucessfully!" );
            } else {
                oOrder.setValueState("Error");
                oCustomer.setValueState("Error");
            }
        }
    });
});
```
Test your application.


### Retrieve data from Northwind service

Go to your View1 XML and remove all the northwind> prefixes in our bindings. Our OData Model is the default model, it means we do not need any prefixed model names when binding unlike what we did with the JSON Model.
```xml
<Table id="idTableOrders" items="{/Orders}">
```

```xml
<ColumnListItem id="idColumnListItem">
	<cells>
		<ObjectIdentifier id="idOrderID" title="{OrderID}" />
		<Text id="idCustomerID" text="{CustomerID}" />
		<Text id="idShipDate" text="{ShippedDate}" />
		<Text id="idShipCountry" text="{ShipCountry}" />
	</cells>
</ColumnListItem>
```


Test your application. 
