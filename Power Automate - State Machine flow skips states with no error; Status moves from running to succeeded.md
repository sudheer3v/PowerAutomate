# Power Automate - State Machine flow skips states with no error; Status moves from running to succeeded.

In this article we talk about:
- An issue I faced with State Machine Workflow.
- How to identify it.
- What is the resolution for this issue.

### Details about State Machine Flow:
As you may already know, Power Automate accomplishes State Machine flow concept by wrapping a Switch Statement inside of a Do Until action. The Switch statement lets you transition from one Case to another until a certain condition is met, which will exit the Do Until. In order to configure the Do Until, you must first create a variable to use for the escape value like Status = New. Below you can see that the Do Until will continue to run until the “Status” variable is “Completed.”

### Issue: 
- Here in my State Machine I have 5 Cases and each case will have an approver. When Case 1 approver approves then it goes to 
 
Also, note the Timeout value for the Do Until action. The default value is PT1H (1 Hour), which is 1 hour. Update this as necessary to support your process. The maximum value is P30D (30 Days) or PT720H (Day Converted to hours) (30 days).
 
Each level can potentially need more than 30 days to complete, but that is the easy part, we split the flow in several sub approval flows and after 29 days we restart the sub approval flow: there is no other technical solution, no discussion here.

        <img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA5.png" width=700>
