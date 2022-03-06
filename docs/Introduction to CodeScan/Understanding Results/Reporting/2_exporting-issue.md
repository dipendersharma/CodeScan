## Metadata_Start
## title: Exporting issues to .csv format using the codescan-export tool
## original-url : https://knowledgebase.autorabit.com/docs/exporting-issues-to-csv-format-using-the-codescan-export-tool
## article-id : e1cf2b79-d4cf-4a54-b67d-d8ffae5a1b23
## seo-title : 
## description : 
## Metadata_End
This guide will walk you through the steps necessary to export a **.CSV** report of your projects issues.

### Requirements:

* A Bash terminal (such as Git Bash)
* The [codescan-export tool](https://www.npmjs.com/package/codescan-export){target="_blank"} (This can be acquired through Node.JS or git)
* Your Codescan credentials:

    * [Organization Key](https://knowledgebase.autorabit.com/codescan/docs/finding-your-organization-key){target="_blank"}
    * [Project Key](https://knowledgebase.autorabit.com/codescan/docs/how-to-find-a-project-key-in-codescan){target="_blank"}
    * [Security Token](https://knowledgebase.autorabit.com/codescan/docs/generating-a-security-token){target="_blank"}

The plugin can be used by simply calling it from the CLI and feeding it the required parameters. 

Enter the following command to see a list of options.
```
codescan-export -h
```
#### Example, usage of the plugin to pull all issues:
:::(Info) (Note:)
The API is limited to returning **10,000** results at once; due to this you may need to segment your issues into multiple reports.
:::
```
codescan-export MyOrganizationKey MyProjectKey --token=MyToken -f C:/MyDirectory/MyFileName.csv
```
#### Example, usage of the plugin to pull all issues with the severity of blocker or critical:
```
codescan-export MyOrganizationKey MyProjectKey --token=MyToken --types=BUG --severities=BLOCKER,CRITICAL -f C:/MyDirectory/MyFileName.csv
```
