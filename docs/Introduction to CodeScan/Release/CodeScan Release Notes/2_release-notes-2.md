## Metadata_Start
## title: Release Notes 22.2
## original-url : https://knowledgebase.autorabit.com/docs/release-notes-222
## article-id : d76586eb-a0cf-40f9-b6c6-f4cd2a2a520a
## seo-title : 
## description : 
## Metadata_End
## CodeScan 22.2
**Released Date: 26 Jan 2022**

### New Features

* **New compliance rules added for Apex Class**: 

    * **Long Class Names**: In the Apex class ruleset, we have added a new rule “Long Class Name” You can now configure an Apex Class with a class name that is longer than 40 characters.

    * **Long Trigger Names**: In the Apex class ruleset, we have added a new rule “Long Trigger Name”. You can now configure an apex trigger with a trigger name that contains more characters than the set limit.

    * **Long Method Name**: In the Apex class ruleset, we have added a new rule “Long Method Name”. This rule helps to create an apex class rule with a method name that contains more characters than a set limit.

* **New compliance rules added for Salesforce Metadata**: 

    * **Avoid Excess Workflow Rules in Org**: In the Salesforce metadata ruleset, we have added a new rule “Avoid Excess Workflow Rules in Org”. This rule helps to limit the number of workflow rules in your salesforce org.

* **Project Analysis Log Report**: We've added a new feature that allows users to view their project analysis report by clicking on a link from their VC project. As a result, the user can now view the detailed log report.

### Enhancements

*  **Log4j Version**: Updated the latest version of log4j to 2.17.1 to address the Apache Log4j security vulnerabilities.

* **Scheduled project reports**: Users with Administrator permission either at the project level or organization level can configure the scheduled project reports. Earlier, this option was available only to the owners of the organization.

* **Analyze salesforce packages**: Users can now analyze the contents of salesforce packages. This will help to keep track of issues in files packages. This feature is especially helpful when the packages are developed and maintained by the user.

### Bug Fixes

* There was an issue with project reports not being triggered when they were scheduled; this has now been fixed.
