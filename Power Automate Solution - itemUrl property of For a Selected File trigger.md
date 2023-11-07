# Power Automate Solution - itemUrl property of "For a Selected File" trigger fails to open the file in Desktop App.

#### Issue Description: 
When you use itemUrl value of "For a Selected File" trigger in an email or anywhere else, when you click that link it always opens the file in web browser, even if you setup your SharePoint Library settings to open all the files in Client Application.
In this article we will talk about a workaround for this itemUrl issue.

1. First go to flow.microsoft.com and login with your credentials
2. Next I selected Create on my left navigation and selected Automated Cloud Flow as shown below.
        <img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA1.png" width=600>
3. Now it asked me to enter name of the flow and to choose the flow's trigger.
4. Here I chose a SharePoint trigger called *When a file is created (Properties Only)* trigger and clicked on `Create` button.
      <img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA2.png" width=600 align=center>
6. Now I am inside the flow where I can add actions and build my flow as I need.
7. Now I add the Site Address and Library Name. Next I added a trigger condition in trigger settings to go there I clicked on the `...` (three dots/ellipses).
8. This extended a menu of options and I selected `Settings` in here. Please see the image below for reference.
        <img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA3.png" width=600>
8. This opened the settings page for this trigger and at the bottom of the screen I clicked on `+ Add` option which opened a new text box for entering my condition.
9. In that box I entered this condition `@startsWith(triggerOutputs()?['body/{FilenameWithExtension}'],'Test')` and clicked on `Done`.
        <img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA4.png" width=500>
10. you have to have atleast one trigger and one action to save the flow. Once you complete your flow. Click on `Save` button to save and `Test` button to test. Please see the below image for reference.
        <img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA5.png" width=700>

