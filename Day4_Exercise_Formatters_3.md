# Day 4 Exercise - 3
This is a reference of Code for Day 4 Exercise.

## Day 4 Exercise – Formatters
In this exercise we will add a new Column Required Date and change the date pattern.

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

