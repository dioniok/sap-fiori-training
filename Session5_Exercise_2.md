# Session 5 Exercise - 2
This is a reference of Code for Session 5 Exercise.

## Session 5 Exercise – Binding the details view
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

## Create Order
In this step we will create a post request to backend. 

### Add the MessageBox as module.
On your controller file add the MessageBox library and declare it as global variable

```js
sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/m/MessageToast",
    "zbootcamp/model/formatter",
    "sap/ui/model/Filter",
    "sap/ui/model/FilterOperator",
    "sap/ui/model/Sorter",
    "sap/m/MessageBox" //Add MessageBox
],
/**
 * @param {typeof sap.ui.core.mvc.Controller} Controller
 */
function (Controller, MessageToast, Formatter, Filter, FilterOperator, Sorter, MessageBox) { //Add MessageBox
```

### Create a new button for create
In your ``View1 xml``, add a new button for Create inside the OverflowToolbar of the table.

```xml
  <OverflowToolbar id="idHeaderToolbar">
    <Title id="idTitle" text="Orders (6)" />
    <ToolbarSpacer id="idHdrToolBarSpacer"/>
    <!--Create new button Add-->
    <Button id="idCreateBtn" press="onCreate" icon="sap-icon://add"/>
    <Button id="idSortBtn" press="onSort" icon="sap-icon://sort"/>
  </OverflowToolbar>
```

Create a new function ``onCreate``. Create the data and get the model and use method create to send a POST request to backend. 
```js
onCreate: function(){
    var data = {
        OrderID: 10448,
        CustomerID: "RICAR",
        ShipVia: 2
    };
    var odataModel = this.getView().getModel();
    odataModel.create("/Orders", data, {
        success: function(data, response){
            MessageBox.success("Data successfully created");
        },
        error: function(error){
            MessageBox.error("Error while creating the data");
        }
    });
}
```

Test your application. 
