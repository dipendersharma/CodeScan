## Metadata_Start
## title: Creating Custom Rules with XPath for Self-Hosted CodeScan
## original-url : https://knowledgebase.autorabit.com/docs/creating-custom-rules-with-xpath-for-self-hosted
## article-id : d8efaf1c-5d5c-4e4e-ad15-b7687c6ba964
## seo-title : Creating Custom Rules with XPath for Self-Hosted CodeScan
## description : CodeScan allows you to create custom rules using XPath. Find out the special requirements where you can use these rules to trigger violations.
## Metadata_End
[CodeScan](https://www.codescan.io/){target="_blank"} allows you to create custom rules using XPath. You can use these rules to trigger violations based on any special requirements you may have.
![Video](https://vimeo.com/238016188){height="480" width="640"}
:::(Info) (Note:)
1. The custom XPath Visualforce rule template uses **XPath version 2** whereas the custom XPath Apex rule template uses **XPath version 1**.
2. This needs to be changed in the designer as the rules are being developed or could introduce bugs.
:::
## Requirements:

* You will need a good working knowledge of XPath to get this working.
* Head over to the [downloads](https://www.codescan.io/products/cloud/#self-hosted){target="_blank"} page and download the **Apex-Custom Rule Designer**.

## Apex
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

## VisualForce

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
