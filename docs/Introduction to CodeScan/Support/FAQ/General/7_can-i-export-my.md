## Metadata_Start
## title: Can I export my test results?
## original-url : https://knowledgebase.autorabit.com/docs/can-i-export-my-test-results
## article-id : 2408c8f5-6c9a-4490-a4b2-7600b16e4065
## seo-title : CodeScan Self Hosted | CodeScan Cloud
## description : CodeScan by AutoRABIT is a static code analysis solution for Salesforce DevOps teams. Visit here to learn how to export your test results for easy sharing.
## Metadata_End
Yes you can. To export to a **.CSV file**, you can use our **.CSV export tools**.

To export results for CodeScan Cloud or [CodeScan Self-Hosted](https://www.codescan.io/products/self-hosted/){target="_blank"}, you can use our npm tool. Find out more click [here](https://www.npmjs.com/package/codescan-export){target="_blank"}.

If you would like a GUI tool for Self-Hosted, you can use our CSV plugin. See below for details.

## Installation

:::(Info) (Note:)
The .CSV plugin requires a SonarQube™ (**6.5+**) installation.
:::

* First, you need to download the **.CSV export plugin** from [here](https://github.com/VillageChief/sonarqube-csv-export-plugin/releases/tag/v0.4.0){target="_blank"}. It’s available as a ready-to-go **.JAR file** or an archive of source code (**.ZIP** and **.TAR.GZ**) .

* Copy the **.JAR file** into your SonarQube™ plugins folder at “(your SonarQube™ directory)/extensions/plugins/“.

Start your SonarQube™ server and run a scan on one or more projects. Once the scan is finished, click on the **More** drop-down menu at the top of the screen. Click on **CSV Issue Export** and you’ll be given a list of fiters and all projects currently in SonarQube™.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28368%29.png){height="" width=""}

Choose the filters you require and click the name of a project to download the **.CSV report** for that project with the filters you have selected. Open the file with a spreadsheet editor to view your project's issues.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28369%29.png){height="" width=""}

There is a limit of **10,000** issues per export. If this occurs, please add filters to narrow your selection.
