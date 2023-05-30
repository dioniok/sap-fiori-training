# Session 2 Exercises - 1
This is a reference of Code for Session 2 Exercise.

## Session 2 Exercise - Create Display Orders Page
In this exercise we will create the Display Orders Page.

### How to Format Code
You may use `Shift + Alt + F` to format your code in your JS and XML files. 

### Change Application Title
Go to your `i18n.properties` file and update the `appTitle` and  `title`.

```csv
#XTIT: Application name
appTitle=Display Orders

#YDES: Application description
appDescription=A Fiori application.
#XTIT: Main view title
title=Display Orders
```

### Create the Filter Bar 

Reference the `sap.ui.comp.filterbar` in the `View1.view.xml`.
```xml
<mvc:View controllerName="zbootcamp.controller.View1" xmlns:mvc="sap.ui.core.mvc" displayBlock="true" xmlns="sap.m" xmlns:filterbar="sap.ui.comp.filterbar">
```

Add the `<filterbar>` with `Order ID` and `Customer ID` fields inside the `<content>` in the `View1.view.xml`.
```xml
<content>
 <filterbar:FilterBar id="idFilterBar">
      <filterbar:filterGroupItems>
          <filterbar:FilterGroupItem id="idFilterGrpItmOrder" name="order" groupName="a" visibleInFilterBar="true" label="Order ID">
              <filterbar:control>
                  <Input id="idOrder"/>
              </filterbar:control>
          </filterbar:FilterGroupItem>
          <filterbar:FilterGroupItem id="idFilterGrpItmCust" name="customer" groupName="a" visibleInFilterBar="true" label="Customer ID">
              <filterbar:control>
                  <Input id="idCustomer"/>
              </filterbar:control>
          </filterbar:FilterGroupItem>
      </filterbar:filterGroupItems>
  </filterbar:FilterBar>
</content>
```
Test your application.

### Create the Table 
Add the `<Table>` inside the `<content>` after the `<filterbar>`.
```xml
<Table id="idTableOrders">
 <headerToolbar>
     <OverflowToolbar id="idHeaderToolbar">
         <Title id="idTitle" text="Orders (6)" />
     </OverflowToolbar>
 </headerToolbar>
 <columns>
     <Column id="idColumnOrder">
         <Text id="idTextOrder" text="Order" />
     </Column>
     <Column id="idColumnCustomer">
         <Text id="idTextCustomer" text="Customer" />
     </Column>
     <Column id="idColumnShipDate">
         <Text id="idTextShipDate" text="Ship. Date" />
     </Column>
     <Column id="idColumnShipCountry">
         <Text id="idTextShipCountry" text="Ship. Country" />
     </Column>
 </columns>
 <items>
     <ColumnListItem id="idColumnItem1">
         <cells>
             <ObjectIdentifier id="idOrder1" title="10250" />
             <Text id="idCustomer1" text="HANAR" />
             <Text id="idShipDate1" text="July 12, 1996" />
             <Text id="idShipCountry1" text="Brazil" />
         </cells>
     </ColumnListItem>
     <ColumnListItem id="idColumnItem2">
         <cells>
             <ObjectIdentifier id="idOrder2" title="10251" />
             <Text id="idCustomer2" text="VICTE" />
             <Text id="idShipDate2" text="July 15, 1996" />
             <Text id="idShipCountry2" text="France" />
         </cells>
     </ColumnListItem>
     <ColumnListItem id="idColumnItem3">
         <cells>
             <ObjectIdentifier id="idOrder3" title="10252" />
             <Text id="idCustomer3" text="SUPRD" />
             <Text id="idShipDate3" text="July 11, 1996" />
             <Text id="idShipCountry3" text="Belgium" />
         </cells>
     </ColumnListItem>
     <ColumnListItem id="idColumnItem4">
         <cells>
             <ObjectIdentifier id="idOrder4" title="10253" />
             <Text id="idCustomer4" text="HANAR" />
             <Text id="idShipDate4" text="July 16, 1996" />
             <Text id="idShipCountry4" text="Brazil" />
         </cells>
     </ColumnListItem>
     <ColumnListItem id="idColumnItem5">
         <cells>
             <ObjectIdentifier id="idOrder5" title="10254" />
             <Text id="idCustomer5" text="CHOPS" />
             <Text id="idShipDate5" text="July 23, 1996" />
             <Text id="idShipCountry5" text="Switzerland" />
         </cells>
     </ColumnListItem>
     <ColumnListItem id="idColumnItem6">
         <cells>
             <ObjectIdentifier id="idOrder6" title="10255" />
             <Text id="idCustomer6" text="RICSU" />
             <Text id="idShipDate6" text="July 15, 1996" />
             <Text id="idShipCountry6" text="Switzerland" />
         </cells>
     </ColumnListItem>
 </items>
</Table>
```
Test your application.

### Create the Footer
Add `<footer>` after `<content>` and create a `Process Order Button`.
```xml
 <footer>
     <OverflowToolbar id="idFooterToolBar">
         <content>
             <ToolbarSpacer id="idToolBarSpacer"/>
             <Button id="idProcessBtn" text="Process Order" type="Emphasized" />
         </content>
     </OverflowToolbar>
 </footer>

```
Test your application.

