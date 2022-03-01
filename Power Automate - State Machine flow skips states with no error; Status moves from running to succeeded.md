# Power Automate - State Machine flow skips states with no error; Status moves from running to succeeded.

In this article we talk about:
- Introduction
- An issue I faced with State Machine Workflow
- How I identified it
- Resolution for this issue

### Introduction:
#### What is State Machine?
Power Automate offers a template that supports the concept of a State Machine. A State Machine provides the ability to model your workflow in an event-driven manner.
    
<img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/SMF_DoUntil_Issue/StateMachineFlowTemplate.JPG" width=700>
<img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/SMF_DoUntil_Issue/StateMachineSkeleton.JPG">

As you may already know, Power Automate accomplishes State Machine flow concept by wrapping a Switch Statement inside of a Do Until action. The Switch statement lets you transition from one Case to another until a certain condition is met, which will exit the Do Until. Below you can see that the Do Until will continue to run until the “Status” variable is “Completed.”

<img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/SMF_DoUntil_Issue/DoUntil SMF.JPG">

In order to configure the Do Until, you must first create a variable to use for the escape value like Status = New. 

<img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/SMF_DoUntil_Issue/New Status SMF.JPG">


#### My State Machine
In my State Machine flow, I have 5 Cases in my Switch and each case contains an approver. When Case 1 approver approves the Switch will move the flow to Case 2, when case 2 approver approves the switche will move the flow to case 3, this process continues until case 5, in case 5 when the approver approves it goes to Completed Status and the Switch statement will exit the Do Until.

### Issue: 
- I observed that my State Machine flow is skipping some cases in the Switch. 
- The workflow status is directly changing to Succeeded instead of staying in running.
- When previous case approver approves, it should change the status to next case and send an email to next approver, in my case the status is changing but the next approver is not receiving any email. 
- The next approver is not seeing any tasks assigned in Action Items.

### Resolution:
- After enough research I found this article https://www.c-sharpcorner.com/blogs/develop-state-machine-workflow-using-power-automate-in-sharepoint-online that mentioned about Do Until action time limit.
- There is a Timeout value for the Do Until action. The default value is PT1H (1 Hour), which is 1 hour. 
- This means, if an approver cannot approve his case with in 1 hr then the Do Until action will time out and the Switch case will not move to next case.
- We need to update this as necessary to support your process. The maximum value is P30D (30 Days) or PT720H (Day Converted to hours) (30 days).
- Once I updated this to PT700H. Then it started working as expected.
 


        
