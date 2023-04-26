# Session 5 Exercise - 3
This is a reference of Code for Session 5 Exercise.

## Session 5 Exercise – Routing
In this step we will apply the changes we have done in the slides for Routing.

### Add Navigation to Item
Add an itemPress event in the Table and name it onItemPress.

```xml
 <Table id="idOrders" items="{/Orders}" itemPress="onItemPress">
```

Add a type in the ColumnListItem and set the value to Navigation.
```xml
<ColumnListItem type="Navigation">
```

### Create a new View 
Create a new view with a simple details page using Simple form control and name it View2.view.xml.

```xml
<mvc:View xmlns:mvc="sap.ui.core.mvc" displayBlock="true" xmlns="sap.m" xmlns:f="sap.ui.layout.form">
	<Page>
		<content>
			<f:SimpleForm title="Order 10248">
				<f:content>
					<Label text="Customer"/>
					<Text text="VINET"/>
					<Label text="Ship Via"/>
					<Text text="Federal Shipping"/>
					<Label text="Ship Date"/>
					<Text text="July 16, 1996"/>
					<Label text="Ship Country"/>
					<Text text="France"/>
				</f:content>
			</f:SimpleForm>
		</content>
	</Page>
</mvc:View>
```

### Add a new route and target
Go to your manifest.json file and add the new route and target for View2.

```js
"routes": [
	{
	  "name": "RouteView1",
	  "pattern": ":?query:",
	  "target": [
	    "TargetView1"
	  ]
	},
	{
	  "name": "RouteView2",
	  "pattern": "detail",
	  "target": [
	    "TargetView2"
	  ]
	}
],
"targets": {
	"TargetView1": {
	  "viewType": "XML",
	  "transition": "slide",
	  "clearControlAggregation": false,
	  "viewId": "View1",
	  "viewName": "View1"
	},
	"TargetView2": {
	"viewType": "XML",
	"transition": "slide",
	"clearControlAggregation": false,
	"viewId": "View2",
	"viewName": "View2"
	}
}
```
### Add the onItemPress function and add the routing to View2
Add a router navigation to View2 once table item is pressed.
```js
onItemPress: function(){
	var oRouter = this.getOwnerComponent().getRouter();
	oRouter.navTo("RouteView2");
}
```

Test your application.


## Routing with Paramater
In this step we will route to the item page with a parameter. 

### Update routing pattern in manifest
In your manifest.json, update the routing pattern for your detail page route to handle a mandatory parameter called orderId.

```js
{
  "name": "RouteView2",
  "pattern": "detail/{orderId}",
  "target": [
    "TargetView2"
  ]
}
```

### Create a controller for the View2
Under the controller folder, create a new file and name it View2.controller.js.

```js
sap.ui.define([
    "sap/ui/core/mvc/Controller"
],
    /**
     * @param {typeof sap.ui.core.mvc.Controller} Controller
     */
    function (Controller) {
        "use strict";

        return Controller.extend("zbootcamp.controller.View2", {
            
            
           
        });
    });

```

### Update View2 xml with new controller
Open your View2.view.xml file, then set the controllerName attribute of your root <mvc:View> element to its designated controller.

```xml
<mvc:View controllerName="zbootcamp.controller.View2" xmlns:mvc="sap.ui.core.mvc" displayBlock="true" xmlns="sap.m" xmlns:f="sap.ui.layout.form">
```

### Update onItemPress function
Now, we need to update the onItemPress function in View1.controller.js to extract the data from the selected item, and then pass it onto the details page.

```js
 onItemPress: function(oEvent){
    	var oRouter = this.getOwnerComponent().getRouter();
	var oSelectedItem = oEvent.getParameter("listItem");
	var oContext = oSelectedItem.getBindingContext();
	var sOrderId = oContext.getObject("OrderID");

	oRouter.navTo("RouteView2", {
	    orderId: sOrderId
	}, false);
}
```
Test your application.
