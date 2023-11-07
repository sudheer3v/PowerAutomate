# Power Automate Solution - itemUrl property of "For a Selected File" trigger fails to open the file in Desktop App.

#### Issue Description: 
When you use itemUrl value of "For a Selected File" trigger in an email or anywhere else, when you click that link it always opens the file in web browser, even if you setup your SharePoint Library settings to open all the files in Client Application.
In this article we will talk about a workaround for this itemUrl issue.

1. First go to make.powerautomate.com and login with your credentials
2. Select Create on left navigation and select Instant Cloud Flow, Name your flow and select For a Selected File as your trigger and hit Create button. 
        <img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA1.png" width=600>
3. Your flow opens in Edit mode with your trigger on the top, configure your trigger with your Site Address and Library Name.
4. Next, Click New step and choose Get file properties operation, configure the Site Address, Library Name and in the Id field pass the Id value of For a selected file trigger.
      <img src="https://github.com/sudheer3v/PowerAutomate/blob/PowerAutomate_DEV/src/Images/PATriggerConditionforName/PA2.png" width=600 align=center>
6. Now you construct a new URL.
7. In the Email body you can simply concatiante the URL prefix and Full Path property from the Get file properties action. "https://contoso.sharepoint.com/sites/abcs/Full Path" 
8. You can assign this to a variable to reuse.
