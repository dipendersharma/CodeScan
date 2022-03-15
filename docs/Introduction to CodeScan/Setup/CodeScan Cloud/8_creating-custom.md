CodeScan allows you to create custom rules using XPath. You can use these rules to trigger violations based on any special requirements you may have.

1. The custom XPath Visualforce rule template uses **XPath version 2** whereas the custom XPath Apex rule template uses **XPath version 1**.

3. This needs to be changed in the designer as the rules are being developed or could introduce bugs.

## Requirements

* You will need a good working knowledge of XPath to get this working.
* Head over to the [downloads](https://license.code-scan.com/index.php/download/login?path=codescan-cli-4.0.4-designer-jar-with-dependencies.jar){target="_blank"} page and download the **Apex-Custom Rule Designer**. Its a designer tool to help build Xpath Rules.

## Creating Custom Rules

1. Login to your codescan account.
2. Go to your organization and head over to **Quality Profiles** tab.
4. Click on any one of the profile under the **Apex** section.
5. The next screen will display the total numbers of active / inactive rules for your profile. Click on any of the link to take you to the **Rules** tab.
6. Scroll to the bottom of the page to find the **XPath rule template**, or use the search filter for quicker result. 
7. Click on the **XPath rule template** link.
8. Scroll to the bottom of the page on the next screen, and click on **Create** under Custom Rules.
9. On the **Create Custom Rule** pop-up screen, please fill in the basic details like name, key, type, description and add the Xpath query (generated from *Apex-Custom Rule Designer*).
10. Click **Create**.


### Apex
Here are some examples of XPath queries for Apex.

**Naming:**

* XPath queries can be used to catch unwanted trends or enforce standards in the naming of your Classes, Methods, and Variables.
* This query will catch any Class names that do not start with ***PREFIX_***
```
//ClassOrInterfaceDeclaration
[
  not(starts-with(@Image, ‘PREFIX_’))
]
```
This example would catch the first class here:
```
class NewClass{}
class PREFIX_NewClass{}
```

***starts-with*** can also be replaced with:

* ***ends-with*** - This checks for a string at the end of the @Image name.
* ***matches*** - This uses regular expression in the place of the string to check for patterns in the @Image name.

### VisualForce

You can also use this some technique for VisualForce (in the Apex-Custom Rule designer, select the **VisualForce** language and use **XPath 2.0** instead of **XPath 1.0**).

**Naming:**

XPath queries can be used to catch unwanted trends or enforce standards in the naming of your Pages.

This query will catch any Page names that do not start with ***PREFIX_***
```
//Document [@Filename[not(starts-with(.,“PREFIX_”))]]
```
This example would catch the first Filename here, but ignore the second:
```
NewPage.page
PREFIX_NewPage.page
```
***starts-with*** can also be replaced with:

* ***ends-with*** - This checks for a string at the end of the @Image name.
* ***matches*** - This uses regular expression in the place of the string to check for patterns in the @Image name.
