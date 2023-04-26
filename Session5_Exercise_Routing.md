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
<mvc:View controllerName="zbootcamp.controller.View2" xmlns:mvc="sap.ui.core.mvc" displayBlock="true" xmlns="sap.m" xmlns:f="sap.ui.layout.form">
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



Test your application.
