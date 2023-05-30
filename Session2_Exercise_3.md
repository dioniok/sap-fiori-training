# Session 2 Exercises - 3
This is a reference of Code for Session 2 Exercise.

## Session 2 Exercise - Fragments
In this step we will create a Fragment and display a dialog when the Cancel Order button is clicked. 

### How to Format Code
You may use `Shift + Alt + F` to format your code in your JS and XML files. 

### Create Fragment
Right click your `webapp` folder and create a new folder named `fragments`. After creating, right click the `fragments` folder and create a new file `CancelOrder.fragment.xml`. Add the code below to create a Fragment. 
```xml
<core:FragmentDefinition xmlns="sap.m" xmlns:core="sap.ui.core">
   <Dialog id="idCancelDialog" title="Cancel Order"/>
</core:FragmentDefinition>
```

### Attach an Event Handler
Go to your `View1.view.xml` and add a new button `Cancel Order` with press event `onCancelOrder`.
```xml
<Button id="idCancelBtn" text="Cancel Order" press="onCancelOrder"/>
```

### Create Event Function
Go to `View1.controller.js` and create a new function `onCancelOrder`. This function will load the fragment and open the dialog. 
```js
onCancelOrder: function () {
    // create dialog lazily
    if (!this.pDialog) {
        this.pDialog = this.loadFragment({
            name: "zbootcamp.fragments.CancelOrder"
        });
    }

    this.pDialog.then(function (oDialog) {
        oDialog.open();
    });
}
```


Test your application.
