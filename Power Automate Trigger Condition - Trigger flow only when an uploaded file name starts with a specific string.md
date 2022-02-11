# Power Automate - Trigger flow only when an uploaded file name starts with a specific string.

In this article we will cover the below points.
- How to add a trigger condition to a flow. 
- What condition is used when we want to start a flow only when file with specific name is uploaded.

1. First go to flow.microsoft.com and login with your credentials
2. Next I selected Create on my left navigation and selected Automated Cloud Flow as shown below.
        > <img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA1.png" width=700 align=middle>
3. Now it asked me to enter name of the flow and to choose the flow's trigger.
4. Here I chose a SharePoint trigger called *When a file is created (Properties Only)* trigger and clicked on `Create` button. Please see the image below for reference.
<img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA2.png" width=500 align=center>
5. Now I am inside the flow where I can add actions and build my flow as I need.
6. Now I add the Site Address and Library Name. Next I added a trigger condition in trigger settings to go there I clicked on the `...` (three dots/ellipses).
7. This extended a menu of options and I selected `Settings` in here. Please see the image below for reference.
<img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA3.png" width=500 align=center>
8. This opened the settings page for this trigger and at the bottom of the screen I clicked on `+ Add` option which opened a new text box for entering my condition.
9. In that box I entered this condition `@startsWith(triggerOutputs()?['body/{FilenameWithExtension}'],'Test')` and clicked on `Done` button. Please see the below image for reference.
<img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA4.png" width=500 align=center>
10. you have to have atleast one trigger and one action to save the flow. Once you complete your flow. Click on `Save` button to save and `Test` button to test. Please see the below image for reference.
<img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA5.png" width=500 align=center>
