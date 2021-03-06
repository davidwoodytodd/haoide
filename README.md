# Sublime IDE for Salesforce
This plugin supports ```Sublime Text 3``` for windows and OSX (**MUST Change the default Workspace for OSX**, otherwise, the downloaded code will not appeared in the sidebar), not tested for Linux.
**If you think this plugin is helpful, please star this plugin.**

# Change Logs
See [History](https://github.com/xjsender/haoide/blob/master/HISTORY.rst)

# Demo
+ [Install Plugin](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/InstallPackage.gif) 
+ [Create New Project](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/NewProject.gif)
+ [Completions](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/Completions.gif)
+ [Trigger](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/Trigger.gif)
+ [Visualforce Page](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/html.gif)
+ [Execute Rest Test](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/Execute%20Rest%20Test.gif)
+ [Document Reference](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/DocumentReference.gif)
+ [Export Workbooks](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/ExportWorkbooks.gif)
+ [Export Workflow](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/ExportWorkflow.gif)
+ [Retrieve Package.xml](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/RetrievePackage.gif)
+ [Deploy Package.zip](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/DeployZip.gif)
+ [Deploy Package Folder](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/DeployPackageFolder.gif)
+ [Deploy Files to Server](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/DeployFilesToServer.gif)
+ [Save Multiple Files to Server](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/SaveMultipleFilesToServer.gif)
+ [Refresh Folder](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/RefreshFolders.gif)
+ [Convert XML to JSON](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/ConvertXML2JSON.gif)
+ [Build Package.xml](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/BuildPackageXML.gif)
+ [Lighting Component Development](https://github.com/xjsender/SublimeApexScreenshot/raw/master/LightingDevelopment.gif)
+ [More Demos](https://github.com/xjsender/SublimeApexScreenshot)

**Please don't change the password and email in the build-in test org**

# Installation
This plugin is hosted on [package control](https://sublime.wbond.net/packages/haoide), after you [installed the package control](https://sublime.wbond.net/installation#st3), you can install this plugin by searching ```haoide``` in package control

# Project Configuration
## Worspace
If your operation system is **OSX**, you must change the workspace in ```HaoIDE``` > ```Setting``` > ```Setting - User``` to override the default workspace.

There are two tiers of workspace concept in this plugin, including plugin level workspace and project level workspace, the privilege level of project level is higher than the plugin level workspace, if you didn't define the workspace in the project property of ```projects``` setting, plugin will set your plugin level workspace to the default workspace, for example, if the settings is set as below:

```javascript
{
    // Workspace in OSX is different with windows, 
    // workspace can be "/Users/<Your User>/salesforce/workspace"
    "workspace": "c:/salesforce/workspace1",
    "projects": {
        "pro-exercise": {
            "default": true,
            "login_url": "https://login.salesforce.com",
            "password": "******",
            "username": "mouse@exercise.com",
            "workspace": "c:/salesforce/workspace2",
        }
    }
}
```

Your plugin level workspace is ```c:/salesforce/workspace1```, your project level workspace is ```c:/salesforce/workspace2```, because you have defined your project level workspace, so the default workspace of ```pro-exercise``` project is ```c:/salesforce/workspace2```, however, if the settings is set as below,

```javascript
{
    // Workspace in OSX is different with windows, 
    // workspace can be "/Users/<Your User>/salesforce/workspace"
    "workspace": "c:/salesforce/workspace1",
    "projects": {
        "pro-exercise": {
            "default": true,
            "login_url": "https://login.salesforce.com",
            "password": "******",
            "username": "mouse@exercise.com",
            "workspace": "c:/salesforce/workspace2",
        },

        "sandbox-exercise": {
            "default": true,
            "login_url": "https://login.salesforce.com",
            "password": "******",
            "username": "mouse@exercise.com"
        }
    }
}
```

Your plugin level workspace is ```c:/salesforce/workspace1```, because ```pro-exercise``` has its own workspace and ```sandbox-exercise``` doesn't have, so, the workspace of ```pro-exercise``` is ```c:/salesforce/workspace2```, the workspace of ```sandbox-exercise``` is ```c:/salesforce/workspace1```


## Projects
There is a default test org in this plugin, you can see it by clicking ```HaoIDE``` > ```Switch Project``` in the main menu, however, if you want to use this plugin in your own org, you need to configure your org user confidential before new project.

In order to prevent plugin update overriding your settings, you should keep your customize settings into ```Setting - User``` by clicking ```HaoIDE``` > ```Settings``` > ```Setting - User```.

You can setup your projects follow below sample by clicking ```HaoIDE``` > ```Settings``` > ```Setting - User``` in the main menu, projects must be included in {}.

When you initiate your settings, you can have more than one project in "projects", however, only one project default should be true.

If your own org login need security token, just set it as sample.

Every time you want to switch the project, you can click ```HaoIDE``` > ```Switch Project``` in the main menu and choose that you want, and then the updated projects settings will be saved to user settings.

If you want to check the current active project, you can check the most left of side bar or press <kbd>ALT</kbd>+<kbd>S</kbd>

After your project configuration is finished, you can click ```HaoIDE``` > ```New``` > ```new project``` in the main menu to download your code.
```javascript
{
    // In OSX, the worspace path is different with windows,
    // for example, workspace in OSX could be "/Users/<Your User>/salesforce/workspace"
    "workspace": "d:/ForcedotcomWorkspace",
    "projects": {
        "Project1 Name": {
            "default": true,
            "login_url": "https://test.salesforce.com",
            "password": "a",
            "username": "a@a.com",

            // If you have security token, just put it here
            "security_token": "12sad3223adfas",

            // Allowed Package Names, for example, twitter, weibo etc.
            "allowed_packages": []
        },
        "Project2 Name": {
            "default": false,
            "login_url": "https://test.salesforce.com",
            "password": "b",
            "username": "b@b.com"
        }
        ......
    }
}
```


## New Project
+ This command is used to create new project
+ Once you click this command, a new project will be downloaded and appeared in the sidebar
+ Just after new project is finished, sobject completions will work
+ Project Folder Name Convention: the project name set in user settings append with date literal of today, for example,
if today is ```2013/07/30``` and user settings is 

```javascript
{
    // Workspace in OSX is different with windows, 
    // workspace can be "/Users/<Your User>/salesforce/workspace"
    "workspace": "c:/ForcedotcomWorkspace",
    "projects": {
        "Exercise-Pro": {
            "default": true,
            "login_url": "https://login.salesforce.com",
            "password": "******",
            "username": "mouse@exercise.com"
        }
    }
}
```
your project folder name should be ```Exercise-Pro-20130730```, you can close this time suffix feature by setting ```keep_project_name_time_suffix``` to false

**If you are developing a package, you need to add your package namespace to settings ``allowed_packages``, more detail to check the ``allowed_packages`` in the default settings**

## Update Project
You can click ```haoide > Update > Update Project``` in the main menu or press <kbd>Alt</kbd>+<kbd>R</kbd> to update your active project.

## Completions:
+ [x] Standard Class Completion
+ [x] sObject Fields Completion and sObject Relationship Completion
+ [x] Relationship Fields Completion
+ [x] Custom Class Completion
+ [x] Input any Character, Show All Standard sObject, Custom sObject, Standard Class and Custom Class
+ [x] After input ``Page.``, list all custom visualforce page
+ [x] Picklist Value Completion
+ [x] SOQL Fields Completion
+ [x] Standard Visualforce Component and Custom Visualforce Component Completion
+ [x] HTML Elements Completion
+ [x] HTML and Visualforce Component Attribute Completion
+ [x] HTML and Visualforce Component Attribute Value Completion
See [Completions Demo](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/Completions.gif)

## Execute Anonymous
Choose any apex code snippet, press <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>E</kbd> or click ```HaoIDE``` > ```Execute Anonymous```, you will see the result, you should be aware, if anonymous code compile is failed, message will be shown in output panel, just after compile succeed, the executed result will be shown in the new view.

There has a ```log_levels``` setting in the default setting, If you want to change anonymous log levels, you can put your log levels settings into your user setting.

## Execute Query
After any snippet which start with SELECT is chosen, you can press <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Q</kbd> in windows or click ```HaoIDE``` > ```Execute Query```, the queried json result will be formated and shown in a new view.

## Keep Operation History
By default, the operation of ```Execute Query```, ```Describe sObject```, ```Gernate SOQL```, ```Execute Anonymous``` and ```Run Test``` will be kept into the ```.history``` path in current project, you can disable this feature by setting ```keep_operation_history``` to false

## Difference between Deploy to Server and Save to Server
* ```Deploy to Server``` use ```Metdata API``, which can be mainly used to deploy files to other different orgs.
* ```Save to Server``` use ```tooling API```, which can't be used in production org.

## Save component
+ This command is only enabled in salesforce code file of active project
+ After code is updated, click ```HaoIDE``` > ```Save to Server``` in the context menu or press <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>S</kbd>
+ If the saving process failed, the console will be open and automatically hidden in **10** seconds, if you think **10** seconds is not enough to check the error message, you add it up to more by setting ```delay_seconds_for_hidden_output_panel_when_failed```

This command just supports ```ApexClass```, ```ApexPage```, ```ApexComponent``` and ```ApexTrigger```, not support ```StaticResource```, if you want to use it to update static resource, you should use ```Deploy to Server``` to see ```[Update StaticResource](#update-static-resource)``` Part in this page

## Save multiple components
Select the files in the sidebar, click ``haoide`` > ``Deploy Files to Server`` in the sidebar menu.

## Save file to other org
- Select the files in the sidebar, click ``haoide`` > ``Deploy Files to Server`` in the sidebar menu
- Open the file to save, click ``haoide`` > ``Deploy to Server`` in the context menu

## Refresh component
+ This command is only enabled in salesforce code file of active project
+ After code is updated in UI or other IDE, press <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>R</kbd> or click ```HaoIDE``` > ```Refresh From Server``` to refresh it from server.

## Delete component
+ This command is only enabled in salesforce code file
+ If you want to delete it from server, click ```HaoIDE``` > ```Delete From Server```

## New ApexClass
Click ```HaoIDE``` > ```New``` > ```New ApexClass```, choose the predefined template, and then input the class name in the input panel at the bottom, after that, your class will be created.

## New ApexPage
Click ```HaoIDE``` > ```New``` > ```New ApexPage```, and then input the page name in the input panel at the bottom, after that, your page will be created.

After you input # after extension or controller name in visualforce page, plugin will create it for you automatically, see [demo](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/QuickController.gif)

## New ApexComponent
Click ```HaoIDE``` > ```New``` > ```New ApexComponent```, and then input the component name in the input panel at the bottom, after that, your component will be created.

## New ApexTrigger
Click ```HaoIDE``` > ```New``` > ```New ApexTrigger```, choose the sobject on which you will create trigger, and then input the trigger name in the input panel at the bottom, after that, your trigger will be created.

## Create Debug Log
If you want to track the log of any user, click ```HaoIDE``` > ```Debug``` > ```Track Debug Log```, wait for a moment, you will see the user list, choose one and press enter, check the progress in the status bar until succeed message appeared, and then your debug log user is recorded.

If you just want to track debug log of yourself, you can click click ```HaoIDE``` > ```Debug``` > ```Track Self Debug Log```.

There is a default ```trace_flag``` settings that is used to define the debug log level in the default settings, you can put your own change into your user settings.

## Fetch Debug Log
If you want to see the log list of any user, click ```HaoIDE``` > ```Apex Test``` > ```Fetch Debug Logs```, wait for a moment, you will see the user list, choose one and press <kbd>enter</kbd>, check the progress in the status bar until succeed message appeared, and then a new view with the log list will be open.

You can choose the ```Log Id``` and click ```HaoIDE``` > ```View Debug Log In Sublime``` command in the context menu, wait for the end of the progress on the status bar, after it is finished, a new view with the log detail will be opened.

Or, you can choose any Log Id and click ```HaoIDE``` > ```View Id In Salesforce Web```, wait for a moment, browser will be open and redirect to the log detail page.

## View Debug Log Detail
Put the focus in the ```Log Id```, press <kbd>alt</kbd> and click left button, the debug log detail will be retrieved and displayed in the new view.

## Run Test
There are two methods to run test, one is by Main Menu, other is in the context menu
By Main Menu: click ```HaoIDE``` > ```Debug``` > ```Run Test```, choose the test class and press <kbd>enter</kbd>, check the progress in the status bar until succeed message appeared, and then a new view with the test result will be open.
By Context Menu: in the context of opened class, click ```HaoIDE``` > ```Run Test Class```, check the progress in the status bar until succeed message appeared, and then a new view with the test result will be open.

## View Code Coverage
This feature just works when api version is >= 29.0
In the context menu of open class or trigger, click ```HaoIDE``` > ```View Code Coverage``` in the context menu, ait for the end of the progress on the status bar, you will see the code coverage percentage in the console and a new view with not covered highlight lines.

Put the focus in the ApexClass Name, press ```alt``` and click left button for twice, the code coverage of specified class will be retrieved and displayed in the new view.

## Keep Apex Code Local History
When you save code, this plugin will keep the change after you saved it to server successfully.

You can close this feature by change ```keep_local_history_change``` settings to false and put it into your own ``user settings``

## Refresh Folder
Choose the folders in the side bar and refresh them by click ```haoide > Refresh Folder`` in the sidebar menu

## Salesforce Document Quick Reference
I get the idea idea from [Salesforce Referencee](https://github.com/Oblongmana/sublime-salesforce-reference) and added some feature based on it.

Click the ```HaoIDE``` > ```Document``` > ```Reload Salesforce Reference``` in the main menu, you need to confirm whether continue, after you confirmed it, then wait for a moment until the ```Open Document``` command is enabled, at this moment, you can press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>O</kbd> or Click it to invoke the ```Open Document``` command, nearly all reference api will be shown in the list, you can try to choose any one and it will be opened in browser.

There is default ```docs``` settings, if you want to add some other document reference to here, you can customize it yourself.
```
"docs": {
    "apexcode": {
       "catalog": "Apex",
       "pattern": "*[@Title='Reference'].//TocEntry[@DescendantCount='0'].."
    },
    ...
},
```
+ **apexdoc**: the part in ```http://www.salesforce.com/us/developer/docs/apexdoc/Data/Toc.xml```, you can get the ```apexdoc``` from Salesforce documents link
+ **Apex**: the document prefix in the quick search panel
+ **pattern**: the XPath pattern for parse the content from the response

**You should be aware that every reloading is time-consuming, generally, you should reload it in every salesforce release**

## Refresh Multiply Components
Choose the components you want to refresh, and then Click ```HaoIDE``` > ```Refresh Selected Components``` in the Sidebar Menu

## Delete Multiply Components
Choose the components you want to delete, and then Click ```HaoIDE``` > ```Delete Selected Components``` in the Sidebar Menu

## Quick Goto Component
Put the focus in the Class Name, and then, press <kbd>shift</kbd>,  and click ```button1``` for twice, the class file will be open in background if this class file is exist, however, if you want to open this class in the foreground, you should press <kbd>shift</kbd> and click ```button1``` for triple.

## Retrieve All Metadata
Click ```HaoIDE``` > ```Metadata Migration``` > ```Retrieve All``` in the main menu, you will see a new open view with message, this view will be refreshed every five seconds, after the retrieve status is completed, plug-in will download the base64 zipfile, after that, base64 zipfile will be decoded to zip file, at the last, this zip file will be extracted.

**This feature is not good enough, because there is no listPackage feature supported, for example, report and dashboard can't be retrieve if no detail folder/report is specified in package.xml**

## Retrieve Package.xml
Click ```HaoIDE``` > ```Metadata Migration``` > ```Retrieve Package.xml``` in the main menu, input your package file path, after that, you will see the effect.

see [Retrieve Package.xml Demo](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/RetrievePackage.gif)

Actually, you can open any package.xml file in the sublime and click ``haoide`` > ``Retrieve Package.xml`` command in the context menu to retrieve specified metadata from default project.

## Update Static Resource
Choose the resource that you need to update in the side bar, firstly, you need to click ``haoide`` > ``Extract To Here`` to extract it to sub folder of ``staticresources``, after you made some change in the extracted folder, choose the extracted folder name and click ``haoide`` > ``Update StaticResource`` in the context menu to save it to server.

You can even use this command to extract any other zip file not limited to Salesforce StaticResource.

see [UpdateStaticResource](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/UpdateStaticResource.gif)

## Deploy
There has a setting ``switch_back_after_migration`` to control whether switch back to original project after deploy is finished, default value is ``true``

### Deploy Package Zip
Click ```HaoIDE``` > ```Metadata Migration``` > ```Deploy Package.zip``` in the main menu, input your zip file path, after that, you will see the effect.

see [Deploy Package Demo](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/DeployZip.gif)

### Deploy Files to Server
Choose the files to deploy and click Click ```HaoIDE``` > ```Deploy File to Server``` in the context menu, you will see the effect

### Deploy Open Files
Sometimes, when you want to deploy class, page or somethings else, however, you didn't want to choose them in the sidebar when there are huge number of code files, you can open the files that you want to deploy to server and Click ```HaoIDE``` > ```Metadata Migration``` > ```Deploy Open Files``` in the main menu to deploy multiply files to target server. 

Actually, you can even open code files in different orgs and deploy them to the same org, for example, there have three classes to be deployed, A and B are in UAT environment and they are newly developed feature, C in UAT environment is completely different with production environment and there is urgent bug needed to be fixed in production, so at this moment, you can open A and B classes in UAT and the fixed version of C class in production and click ```Deploy Open Files``` to deploy the three class from different orgs to production environment.

This command is just enabled when any one of open files is salesforce code files.

### Deploy Package Folder
Choose a valid package folder, click right button, check if the ```Deploy to Server``` command is enabled, if yes, it means the package folder is valid, and then click the ```Deploy To Server`` command, you will see the effect.

see [Deploy Package Folder](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/DeployPackageFolder.gif)

## Export
You can export somethings in your org to CSV by these features

### Export CustomFields
You can click ```HaoIDE``` > ```Export``` > ```Export CustomField``` to export all custom fields in your org to csv.

### Export Workflow Rules
After you downloaded all metadata by clicking ```HaoIDE``` > ```Metadata Migration``` > ```Retrieve Sobject And Workflow```, you can click ```HaoIDE``` > ```Export``` > ```Export Workflow``` to backup all workflows in your org to csv.

If you just want to export some attributes of workflows, you can remove some columns in the ```workflow_rule_columns```, ``workflow_field_update_columns``, ``workflow_email_alert_columns``, ``workflow_outbound_message_columns`` and ``workflow_task_columns`` settings and put it into your own user settings.

### Export Validation Rules
After you downloaded all metadata by clicking ```HaoIDE``` > ```Migration``` > ```Retrieve Sobject And Workflow```, you can click ```HaoIDE``` > ```Export``` > ```Export Validation Rule``` to backup all validation rules in your org to CSV.

If you just want to export some attributes of validation rules, you can remove some columns in the ```validation_rule_columns``` setting and put it into your own user settings

### Export CustomFields
You can click ```HaoIDE``` > ```Export``` > ```Export CustomFields``` to export all custom fields in your org to CSV.

### Export Profile Workbook
You can click ```HaoIDE``` > ```Export``` > ```Export Profile``` to export ```ObjectPermission```, ```TabVisibilities``` and ```UserPermissions``` of all profiles to three different CSV files, see [ObjectPermission CSV Picture](https://raw.githubusercontent.com/xjsender/SublimeApexScreenshot/master/Profile.png)

Before execute this command, you should execute the ```Retrieve All``` command to download all related components.

### Export Workbook of sobjects
You can click ```HaoIDE``` > ```Export``` > ```Export Workbook``` to export all sObject workbooks or some sObject separated with semi-colon in your org to CSV.

If you just want to export some attributes of sobject workbook, you can remove some columns in the ```workbook_field_describe_columns``` setting and put it into your own user settings

### Export Data Template
Click ```HaoIDE``` > ```Export``` > ```Export Data Template```, wait for a moment, choose the record type of sobject, the sobject data template by record type will be exported. From the row 1 to row 6, meaning is show as below,
```
[Field Label]...
[Field API]...
[Field Type]...
[Layout Required]...
[Picklist Label if has]...
[Picklist Value if has]
```

## Utilities
There are some utilities to keep your work efficient as below

### Convert 15Id to 18Id
You can click ```HaoIDE``` > ```Utilities``` > ```Convert 15Id to 18Id``` to convert your input 15Id to 18Id, if your input is not valid 15Id, it will be returned as original value

### Describe sObject
Click ```HaoIDE``` > ```Utilities``` > ```Describe sObect```, and then choose a sObject in the selection panel and press <kbd>Enter</kbd>, the describe result will appear in the new view

### Generate sObject SOQL
Click ```HaoIDE``` > ```Utilities``` > ```Generate sObject SOQL```, and then choose a sObject in the selection panel and press <kbd>Enter</kbd>, the sObject SOQL will appear in the new view

### Pretty JSON
Click ```HaoIDE``` > ```Utilities``` > ```JSON Pretty```, and then input your JSON Body in the input panel and press <kbd>Enter</kbd>, the Prettied JSON will appear in the new view

### Serialize JSON
Click ```HaoIDE``` > ```Utilities``` > ```JSON Serialization```, and then input your JSON Body in the input panel and press <kbd>Enter</kbd>, the Serialized JSON will appear in the new view

### Convert JSON to Apex
You can click ```HaoIDE``` > ```Utilities``` > ```Convert JSON to Apex``` to convert your input json to Apex class.

Default class name of main class is ```JSON2Apex```, after you input the JSON to be converted, plugin will ask you to input the class name, you can change the default name there.

In order to keep the accuracy of converted result, you should predefine the every value of every key in the input JSON

#### Notes:
+ [x] If value is matched with ```\d{4}-\d{2}-\d{2}T[\d:Z.]+``` regress expression, data type will be thought as ```DateTime```
+ [x] If value is matched with ```\d{4}-\d{2}-\d{2}``` regress expression, data type will be thought as ```Date```
+ [x] If value is ```null```, data type will be thought as ```Object```

#### Example:
If the json string is as below,
```javascript
{
    "name": "test",
    "birthday": "1982-01-19T09:58:13.190Z",
    "age": 32, 
    "money": 12321.5,
    "createdDate": "2015-01-20",
    "children": [
        {
            "name": "son",
            "age": 2,
            "birthday": "2013-01-19T09:58:13.190Z",
            "money": 0, 
            "toy": [{
                "name": "toy1"
            }]
        },
        {
            "name": "daughter",
            "age": 1,
            "birthday": "2014-01-19T09:58:13.190Z",
            "money": 0,
            "toy": [{
                "name": "toy2"
            }]
        }
    ],
    "father": {
        "name": "father",
        "age": 75,
        "birthday": "1940-01-19T09:58:13.190Z",
        "money": 0
    }
}
```

The converted apex will be as below:
```java
public class Toy {
    public String name;
}

public class Children {
    public String name;
    public List<Toy> toy;
    public Integer age;
    public Integer money;
    public DateTime birthday;
}

public class Father {
    public String name;
    public Integer age;
    public Integer money;
    public DateTime birthday;
}

public class JSON2Apex {
    public List<Children> children;
    public Date createdDate;
    public Integer age;
    public Decimal money;
    public String name;
    public Father father;
    public DateTime birthday;
}

public static JSON2Apex parse(String jsonStr) {
    return (JSON2Apex) JSON.deserialize(jsonStr, JSON2Apex.class);
}

static testMethod void testParse() {
    String json = '{"children": [{"name": "son", "toy": [{"name": "toy1"}], "age": 2, "money": 0, "birthday": "2013-01-19T09:58:13.190Z"}, {"name": "daughter", "toy": [{"name": "toy2"}], "age": 1, "money": 0, "birthday": "2014-01-19T09:58:13.190Z"}], "createdDate": "2015-01-20", "age": 32, "money": 12321.5, "name": "test", "father": {"name": "father", "age": 75, "money": 0, "birthday": "1940-01-19T09:58:13.190Z"}, "birthday": "1982-01-19T09:58:13.190Z"}';
    JSON2Apex obj = parse(json);
    System.assert(obj != null);
}
```

## Lighting Component Development
Support kinds of lighting development, see [lighting component demo](https://github.com/xjsender/SublimeApexScreenshot/raw/master/LightingDevelopment.gif)

## Exceute Rest Test
Up to now, support ```Get```, ```Post```, ```Put```, ```Patch```, ```Delete```, ```Tooling Query```, ```Query```, ```Query All```, ```Head```, ```Retrieve Body```, ```Search``` and ```Quick Search``` methods.

for example, 

+ **Query Sample**, you can input ```SELECT Id, Name FROM Account LIMIT 1``` and choose it, choose the intput SOQL, and then click ```Execute Rest Test``` in the context menu, choose the ```Query``` in the popup menu, wait for a moment, the queried json result will be shown in the new view.
```
{
    'done': True,
    'records': [{
        'Id': '001O000000M1mPwIAJ',
        'Name': '周星驰',
        'attributes': {
            'type': 'Account',
            'url': '/services/data/v30.0/sobjects/Account/001O000000M1mPwIAJ'
        }
    }],
    'totalSize': 1
}
```

+ **Query With Wildcard Character***, you can input ```SELECT * FROM Account LIMIT 1``` and choose it, choose the intput SOQL, and then click ```Execute Rest Test``` in the context menu, choose the ```Query``` in the popup menu, wait for a moment, the queried json result will be shown in the new view.
```
{
    'done': True,
    'records': [{
        'Id': '001O000000M1mPwIAJ',
        'Name': '周星驰',
        ....
        'attributes': {
            'type': 'Account',
            'url': '/services/data/v30.0/sobjects/Account/001O000000M1mPwIAJ'
        }
    }],
    'totalSize': 1
}
```

+ **Tooling Query Sample**, you can input ```SELECT Id, Name FROM ApexClass``` and choose it, choose the intput SOQL, and then click ```Execute Rest Test``` in the context menu, choose the ```Tooling Query``` in the popup menu, wait for a moment, the queried json result will be shown in the new view.

+ **Post Sample**: you can input ```/sobjects/Account``` and choose it, click ```Execute Rest Test``` in the context menu, choose the ```Post``` in the popup menu and input the json ```{"Name": "Test Rest Test"}``` in the input panel, wait for a moment, the inserted new account will be shown in the new view.
```
{
    'errors': [],
    'id': '001O000000MIiSXIA1'
}
```

+ **Get Sample**: input ```/sobjects/Account/001O000000MIiSXIA1``` and choose it, click ```Execute Rest Test``` in the context menu, choose the ```Get``` in the popup menu, wait for a moment, the detail information of the specified Id will be shown in the new view:
```
{
    'BillingAddress': {
        'city': None,
        'country': 'United States',
        ...
    },
    'BillingCity': None,
    'BillingCountry': 'United States',
    'BillingCountryCode': 'US',
    ...
}
```

+ **Delete Sample**: input ```/sobjects/Account/001O000000MIiSXIA1``` and choose it, click ```Execute Rest Test``` in the context menu, choose the ```Delete``` in the popup menu, wait for a moment, the delete result will be shown in the new view:
```
{}
```

+ **Patch Sample**: Sometimes, you want to update some fields of record, you can input ```/sobjects/Account/001O000000MIiSXIA1``` and choose it, click ```Execute Rest Test``` in the context menu, choose the ```Patch``` in the popup menu and input ```{"Name": "Test Path"}``` in the input panel, wait for a moment, the patch result will be shown in the new view:
```
{}
```

+ **Search Sample**: Sometimes, want to test search action, you can input ```FIND {test}``` and choose it, click ```Execute Rest Test``` in the context menu, choose the ```Search``` in the popup menu, wait for a moment, the patch result will be shown in the new view:
```
[{
    'Id': '001O0000001OWv5IAG',
    'attributes': {
        'type': 'Account',
        'url': '/services/data/v29.0/sobjects/Account/001O0000001OWv5IAG'
    }
}]
```

+ **Quick Search Sample**: Sometimes, want to search something, you can input ```test``` and choose it, click ```Execute Rest Test``` in the context menu, choose the ```Quick Search``` in the popup menu, wait for a moment, the patch result will be shown in the new view:
```
[{
    'Id': '001O0000001OWv5IAG',
    'attributes': {
        'type': 'Account',
        'url': '/services/data/v29.0/sobjects/Account/001O0000001OWv5IAG'
    }
}]
```

## Bulk Api
+ Up to now, support close jobs, export, insert, update and delete.
+ You can set the batch size and batch bytes for every batch by put ```maximum_batch_size``` and ```maximum_batch_bytes``` in your user settings, you should be aware, maximum records of single batch is **10K** and maximum bytes of single batch is **1000K**
+ This tool will get your CSV file encoding type by detecting the first **1000** bytes of the CSV file, as a best practice, you should prepare CSV file which encoding type is ```ANSI``` or ```UTF-8```.
+ If you want to insert a CSV file, you'd better open the CSV file in sublime and copy the file path, after you choose the sobject that you want to insert records, this tool will automatically get the file path from the clipboard

## Proxy
Refer to [Request Proxies](http://docs.python-requests.org/en/latest/user/advanced/#proxies)

# Build-in Dependency Lib
+ [requests](https://github.com/kennethreitz/requests)
+ [xmltodict](https://github.com/martinblech/xmltodict)
+ [dateutil](http://labix.org/python-dateutil/)
+ [xmlformatter](https://pypi.python.org/pypi/xmlformatter/)
