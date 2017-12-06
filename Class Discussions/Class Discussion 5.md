MSSA Cohort 3
Course: ISTA-320
Lesson Plan: 05
Name: Lee Sarduy	

Describe the three concerns that the Model-View-ViewModel design pattern addresses.
In this design pattern, the model provides the data used by the app, and the view represents the way in which the data is displayed in the UI. The ViewModel contains the logic that connects the two, taking the user input and converting it into commands that perform business operations on the model, and also taking the data from the model and formatting it in the manner expected by the view.

Describe in detail how the MVVM design pattern works.
Views use data binding to retrieve and display data managed by the ViewModel. The ViewModel retrieves data from the model and formats it for the views. Views send commands to the ViewModel to perform business operations and update data. The ViewModel sends requests to the model to update data.

Describe in detail how data binding works with respect to controls and models.
Using data binding, you can link a property of a control to a property of an object; if the value of the specified property of the object changes, the property in the control that is linked to the object also changes. In addition, data binding can be bidirectional: if the value of a property in a control that uses data binding changes, the modification is propagated to the object to which the control is linked.

Describe the three methods that the ICommand interface defines. What is the purpose of each method? 
CanExecute(). This method returns a Boolean value indicating whether the command can run. Using this method, a ViewModel can enable or disable a command depending on the context. For example, a command that fetches the next customer from a list should be able to run only if there is a next customer to fetch; if there are no more customers, the command should be disabled.
Execute(). This method runs when the command is invoked.
CanExecuteChanged(). This event is triggered when the state of the ViewModel changes. Under these circumstances, commands that could previously run might now be disabled and vice versa. For example, if the UI invokes a command that fetches the next customer from a list, if that customer is the last customer, then subsequent calls to CanExecute should return false. In these circumstances, the CanExecuteChanged event should fire to indicate that the command has been disabled.

What is a data context? Why do we need a data context? What does it do?
A data context is property that can be set at the form or control level that binds the form or control to an object. For example, if a cow object has a name property, and the application is binding a control to name, the data context tells the application that the cow object is where it needs to get the name.