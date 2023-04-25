# Day 2 Exercises - 1
This is a reference of Code for Day 2 Exercise.

## Day 2 Exercise - Create Display Orders Page
In this exercise we will create the Display Orders Page.

### Change Application Title
Go to your i18n.properties file and update the application Title.

```csv
#XTIT: Application name
appTitle=Display Orders

#YDES: Application description
appDescription=A Fiori application.
#XTIT: Main view title
title=Display Orders
```

### Create the Filter Bar 

Reference the filterbar in the View1 xml.
```xml
<mvc:View controllerName="zbootcamp.controller.View1" xmlns:mvc="sap.ui.core.mvc" displayBlock="true" xmlns="sap.m" xmlns:filterbar="sap.ui.comp.filterbar">
```

Add the filterbar with Order ID and Customer ID fields inside the content in the View1 xml.
```xml
<content>
  <filterbar:FilterBar>
      <filterbar:filterGroupItems>
          <filterbar:FilterGroupItem name="order" groupName="a" visibleInFilterBar="true" label="Order ID">
              <filterbar:control>
                  <Input />
              </filterbar:control>
          </filterbar:FilterGroupItem>
          <filterbar:FilterGroupItem name="customer" groupName="a" visibleInFilterBar="true" label="Customer ID">
              <filterbar:control>
                  <Input />
              </filterbar:control>
          </filterbar:FilterGroupItem>
      </filterbar:filterGroupItems>
  </filterbar:FilterBar>
</content>
```

### Create the Table 
Since we have already referenced the sap.m library, we can now add sap.m controls. Add the table inside the content after the filterbar.
```xml
<Table>
  <headerToolbar>
      <OverflowToolbar>
          <Title text="Orders (6)" />
      </OverflowToolbar>
  </headerToolbar>
  <columns>
      <Column>
          <Text text="Order" />
      </Column>
      <Column>
          <Text text="Customer" />
      </Column>
      <Column>
          <Text text="Ship. Date" />
      </Column>
      <Column>
          <Text text="Ship. Country" />
      </Column>
  </columns>
  <items>
      <ColumnListItem>
          <cells>
              <ObjectIdentifier title="10250" />
              <Text text="HANAR" />
              <Text text="July 12, 1996" />
              <Text text="Brazil" />
          </cells>
      </ColumnListItem>
      <ColumnListItem>
          <cells>
              <ObjectIdentifier title="10251" />
              <Text text="VICTE" />
              <Text text="July 15, 1996" />
              <Text text="France" />
          </cells>
      </ColumnListItem>
      <ColumnListItem>
          <cells>
              <ObjectIdentifier title="10252" />
              <Text text="SUPRD" />
              <Text text="July 11, 1996" />
              <Text text="Belgium" />
          </cells>
      </ColumnListItem>
      <ColumnListItem>
          <cells>
              <ObjectIdentifier title="10253" />
              <Text text="HANAR" />
              <Text text="July 16, 1996" />
              <Text text="Brazil" />
          </cells>
      </ColumnListItem>
      <ColumnListItem>
          <cells>
              <ObjectIdentifier title="10254" />
              <Text text="CHOPS" />
              <Text text="July 23, 1996" />
              <Text text="Switzerland" />
          </cells>
      </ColumnListItem>
      <ColumnListItem>
          <cells>
              <ObjectIdentifier title="10255" />
              <Text text="RICSU" />
              <Text text="July 15, 1996" />
              <Text text="Switzerland" />
          </cells>
      </ColumnListItem>
  </items>
</Table>
```

### Create the Footer
Add footer after content and create a Process Order Button.
```xml
<footer>
    <OverflowToolbar>
        <content>
            <ToolbarSpacer />
            <Button text="Process Order" type="Emphasized" />
        </content>
    </OverflowToolbar>
</footer>

```
Test your application.

