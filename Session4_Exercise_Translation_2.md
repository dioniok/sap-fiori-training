# Session 4 Exercise - 2
This is a reference of Code for Session 4 Exercise.

## Session 4 Exercise – Translation
In this exercise we will translate the texts into German

### Create i18n.properties for German texts
Duplicate the i18n.properties file and rename the second one as i18n_de.properties

### Translate to German
Translate the English values in the i18n_de.properties file with German values. You may use any kind of translation service, such as Google Translate.

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
```

### Test the application
Add sap-ui-language=DE to your URL parameters
```csv
Sample Link: https://port8080-workspaces-ws-ss9w8.ap21.trial.applicationstudio.cloud.sap/test/flpSandbox.html?sap-ui-xx-viewCache=false&sap-ui-language=DE#zbootcamp-display
```
Test your application. 
