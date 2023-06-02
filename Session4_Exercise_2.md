# Session 4 Exercise - 2
This is a reference of Code for Session 4 Exercise.

## Session 4 Exercise – Translation
In this exercise we will translate the texts into German

### Update your ``i18n.properties`` file 

```csv
# This is the resource bundle for zbootcamp

#Texts for manifest.json

#XTIT: Application name
appTitle=Display Orders

#YDES: Application description
appDescription=A Fiori application.
#XTIT: Main view title
title=Display Orders

#Filter Bar
filtOrder=Order ID
filtCustomer=Customer ID

#Table Columns
colOrder=Order 
colCustomer=Customer
colShipVia=Ship Via
colShippingDate=Ship. Date
colShippingCountry=Ship. Country

#Buttons
btnProcessOrder=Process Order
btnCancelOrder=Cancel Order

```

### Replace the hardcoded labels in your xml file
Update the label properties using the i18n text values added in ``i18n.properties`` file

```xml
<filterbar:filterGroupItems>
    <filterbar:FilterGroupItem id="idFilterGrpItmOrder" name="order" groupName="a" visibleInFilterBar="true" label="{i18n>filtOrder}">
        <filterbar:control>
            <Input id="idOrder" value="{northwind>/Orders/0/OrderID}"/>
        </filterbar:control>
    </filterbar:FilterGroupItem>
    <filterbar:FilterGroupItem id="idFilterGrpItmCust" name="customer" groupName="a" visibleInFilterBar="true" label="{i18n>filtCustomer}">
        <filterbar:control>
            <Input id="idCustomer" value="{northwind>/Orders/0/CustomerID}"/>
        </filterbar:control>
    </filterbar:FilterGroupItem>
</filterbar:filterGroupItems>        
```
```xml
<columns>
    <Column id="idColumnOrder">
        <Text id="idTextOrder" text="{i18n>colOrder}" />
    </Column>
    <Column id="idColumnCustomer">
        <Text id="idTextCustomer" text="{i18n>colCustomer}" />
    </Column>
    <Column id="idColumnShipDate">
        <Text id="idTextShipDate" text="{i18n>colShippingDate}" />
    </Column>
    <Column id="idColumnShipCountry">
        <Text id="idTextShipCountry" text="{i18n>colShippingCountry}" />
    </Column>
</columns>

```
```xml
<Button id="idProcessBtn" text="{i18n>btnProcessOrder}" type="Emphasized" press="onProcessOrder"/>
<Button id="idCancelBtn" text="{i18n>btnCancelOrder}" press="onCancelOrder"/>
                
```

### Create i18n.properties for German texts
Duplicate the ``i18n.properties`` file and rename the second one as ``i18n_de.properties``

### Translate to German
Translate the English values in the ``i18n_de.properties`` file with German values. You may use any kind of translation service, such as [Google Translate](https://translate.google.com/).

```csv
title=Bestellungen anzeigen
appTitle=Bestellungen anzeigen
appDescription=App Beschreibung

#Filter Bar
filtOrder=Auftragsnummer
filtCustomer=Kundennummer

#Table
colOrder=Auftrag 
colCustomer=Kunden
colShipVia=Versenden per
colShippingDate=Versanddatum
colShippingCountry=Lieferungsland

#Buttons
btnProcessOrder=Prozessauftrag
btnCancelOrder=Bestellung stornieren
```

### Test the application
Add ``sap-ui-language=DE`` to your URL parameters
```csv
Sample Link: https://port8080-workspaces-ws-ss9w8.ap21.trial.applicationstudio.cloud.sap/test/flpSandbox.html?sap-ui-xx-viewCache=false&sap-ui-language=DE#zbootcamp-display
```
Test your application. 
