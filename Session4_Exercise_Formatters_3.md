# Session 4 Exercise - 3
This is a reference of Code for Session 4 Exercise.

## Session 4 Exercise – Formatters
In this exercise we will continue the steps in the slide and add a new Column Required Date and change the date pattern.

### Format Shipped Date
```xml
<ColumnListItem>
    <cells>
        <ObjectIdentifier title="{OrderID}" />
        <Text text="{CustomerID}" />
	 <!-- Format the Shipped Date -->
        <Text text="{path: 'ShippedDate', 
                type: 'sap.ui.model.type.Date',
                formatOptions: {
                    pattern: 'yyyy/MM/dd'
                }}" 
            />
        <Text text="{ShipCountry}" />
    </cells>
</ColumnListItem>
```
### Add new Column ShipVia
```xml
<columns>
    <Column>
        <Text text="{i18n>colOrder}" />
    </Column>
    <Column>
        <Text text="{i18n>colCustomer}" />
    </Column>
	<!-- Add Ship Via -->
    <Column>
        <Text text="{i18n>colShipVia}"/>
    </Column>
    <Column>
        <Text text="{i18n>colShippingDate}"/>
    </Column>
    <Column>
        <Text text="{i18n>colShippingCountry}" />
    </Column>
</columns>
<items>
    <ColumnListItem>
        <cells>
            <ObjectIdentifier title="{OrderID}" />
            <Text text="{CustomerID}" />
		<!-- Add Ship Via -->
            <Text text="{path: 'ShipVia', formatter: '.formatter.getShipperName'}" />
            <Text text="{path: 'ShippedDate', 
                    type: 'sap.ui.model.type.Date',
                    formatOptions: {
                        pattern: 'yyyy/MM/dd'
                    }}" 
                />
            <Text text="{ShipCountry}" />
        </cells>
    </ColumnListItem>
</items>
```
### Create a new file named ``formatter.js`` and add the following code
```js
sap.ui.define([], function () {
	"use strict";
	return {
		getShipperName: function (sId) {
			if (sId === 1) {
				return 'Speedy Express';
			} else if (sId === 2) {
				return 'Speedy Express';
			} else if (sId === 3) {
				return 'Speedy Express';
			} else {
				return sId;
			}
		}
	};
});
```

### Add the formatter in the View1 controller file
```js
sap.ui.define([
    "sap/ui/core/mvc/Controller",
    "sap/m/MessageToast",
    "zbootcamp/model/formatter", //Add formatter
],
/**
 * @param {typeof sap.ui.core.mvc.Controller} Controller
 */
function (Controller, MessageToast, Formatter) { /Add formatter
    "use strict";

    return Controller.extend("zbootcamp.controller.View1", {
        formatter: Formatter, //Add formatter
        
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

### Add new i18n text for Column Required Date
```csv
colRequiredDate=Required Date
```

### Add new Column and Row Required Date
```xml
 <Table items="{/Orders}">
  <headerToolbar>
      <OverflowToolbar>
          <Title text="Orders (6)" />
      </OverflowToolbar>
  </headerToolbar>
  <columns>
      <Column>
          <Text text="{i18n>colOrder}" />
      </Column>
      <Column>
          <Text text="{i18n>colCustomer}" />
      </Column>
      <Column>
          <Text text="{i18n>colShipVia}"/>
      </Column>
      <Column>
          <Text text="{i18n>colShippingDate}"/>
      </Column>
      <Column>
          <Text text="{i18n>colShippingCountry}" />
      </Column>
      <!-- Add Required Date Column -->
      <Column>
          <Text text="{i18n>colRequiredDate}" />
      </Column>
  </columns>
  <items>
      <ColumnListItem>
          <cells>
              <ObjectIdentifier title="{OrderID}" />
              <Text text="{CustomerID}" />
              <Text text="{path: 'ShipVia', formatter: '.formatter.getShipperName'}" />
              <Text text="{path: 'ShippedDate', 
                  type: 'sap.ui.model.type.Date',
                  formatOptions: {
                      pattern: 'yyyy/MM/dd'
                  }}" 
              />
              <Text text="{ShipCountry}" />
              <!-- Add Required Date -->
              <Text text="{RequiredDate}" />
          </cells>
      </ColumnListItem>
  </items>
</Table>
```
# Format the Required Date
Format the RequiredDate and use date pattern MM/dd/yyyy
```xml
 <Text text="{path: 'RequiredDate', 
  type: 'sap.ui.model.type.Date',
  formatOptions: {
      pattern: 'MM/dd/yyyy'
  }}" 
/>
```
Test your application

