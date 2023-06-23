# Session 8 Exercise - 2
This is a reference of Code for Session 8 Exercise.

## Session 8 Exercise – Binding the details view
In this step we will bind the details view.

### Attach a pattern matched event handler
In the onInit function of your View2.controller.js, using our app’s router, attach a pattern matched event handler. 

```js
onInit : function() {
            
  //Creates an instance of the app's router
  var oRouter = this.getOwnerComponent().getRouter();

  //Get the route we want to attach a Pattern Matched event handler
  oRouter.getRoute("RouteView2").attachPatternMatched(this._onRouteMatched, this);

},

_onRouteMatched: function (oEvent) {

  //Handle the route matched event

}
```
### Handle the pattern-matched event
In the _onRouteMatched function of your View2.controller.js, we will now be handling the “pattern-matched” event. Access the event’s arguments, then extract the passed parameter from there.

```js
 _onRouteMatched: function (oEvent) {
                
     //Handle the route matched event
    var oArgs = oEvent.getParameter("arguments");
    var sOrderId = oArgs.orderId;

}
```
### Create element binding
Now that we have the Order ID from the initial screen, we can now use this to create an Element Binding between the selected order and the current view.
```js
 _onRouteMatched: function (oEvent) {
                
     //Handle the route matched event
    var oArgs = oEvent.getParameter("arguments");
    var sOrderId = oArgs.orderId;

    this.getView().bindElement("/Orders(" + sOrderId + ")");

}
```
### Bind the Details View
In order for our element binding to have an effect, we must now replace the hardcoded values found in the details view / second page.
```xml
<mvc:View controllerName="zbootcamp.controller.View2" xmlns:mvc="sap.ui.core.mvc" displayBlock="true" xmlns="sap.m" xmlns:f="sap.ui.layout.form">
	<Page id="detailPage">
		<content>
			<f:SimpleForm id="idForm" title="">
				<f:content>
					<Label id="idLabelCustomer" text="Customer"/>
					<Text id="idTextCustomer" text="{CustomerID}"/>
					<Label id="idLabelShipVia" text="Ship Via"/>
					<Text id="idTextShipVia" text="{path: 'ShipVia', formatter: '.formatter.getShipperName'}"/>
					<Label id="idLabelShipDate" text="Ship Date"/>
					<Text id="idTextShipDate" text="{path: 'ShippedDate', 
					type: 'sap.ui.model.type.Date',
					formatOptions: {
					    pattern: 'yyyy/MM/dd'
					}}" />
					<Label id="idLabelShipCountry" text="Ship Country"/>
					<Text id="idTextShipCountry" text="{ShipCountry}"/>
				</f:content>
			</f:SimpleForm>
		</content>
	</Page>
</mvc:View>
```

Test your application.
