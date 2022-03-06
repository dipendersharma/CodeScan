## Metadata_Start
## title: Installing CodeScan Self-Hosted
## original-url : https://knowledgebase.autorabit.com/docs/installing-codescan-self-hosted
## article-id : a9eb05ca-44d8-4e15-b632-790cd8823cf2
## seo-title : Installing CodeScan Self-Hosted
## description : It's time to get started with AutoRABIT's CodeScan on your self hosted platform! Here's what you need to know about installing this powerful DevOps tool.
## Metadata_End
This guide will get a **fully functional evaluation version** of the enterprise CodeScan running on your own server.

## Prerequisites:

* SonarQube™ 7.9+
* Java 11
* Windows / Mac / Linux
* NodeJS

## Configure the CodeScan license:
You will need this license to download the plugin. 

Click [here](https://license.code-scan.com/){target="_blank"} to go to the license page and request an evaluation license.

## Download

1. Download the latest compatible version from [here](https://knowledgebase.autorabit.com/codescan/docs/codescan-self-hosted-downloads){target="_blank"}. 
:::(Info) (Note:)
Keep in mind that you need to download a version that is compatible with your **SonarJS plugin version**.
:::
2. When downloading you will need to provide your **License Key** or [Subscription Code](https://knowledgebase.autorabit.com/codescan/docs/what-is-a-subscription-code){target="_blank"} and accept our [Terms of Service](https://www.codescan.io/tos/self-hosted/){target="_blank"}.

3. Extract the **zip file**. It contains the **SonarQube™ plugins** and an **ant based tool** to run an analysis with.

## Plugin installation

1. Delete any existing Salesforce plugins from your installation.

2. Ensure your **SonarJS plugin** is compatible with the current CodeScan for Lightning version.  Currently the supported release requires **v 5.2.1** of the **SonarJS plugin**. See [here](https://www.codescan.io/products/cloud/#self-hosted){target="_blank"} for alternatives.
3. Copy **sonar-salesforce-plugin-XXX.jar** and **sonar-codescanlang-plugin-XXX.jar** into your SonarQube™ installation at **/extensions/plugins/**

### Standard setup:

1. When you receive your license, enter it by logging into **SonarQube™** with the credentials **User: admin**, **Password: admin** and, go to **Administrator** at the top right.

3. Click on **General Settings** on the right side.
4. Click on **[CodeScan](https://www.codescan.io/){target="_blank"}** on the list of Categories.
5. Enter your **license** in the text box labelled ‘**CodeScan license**’ (key is "**sf.license.secured**")
6. Click **save**.

## Setting up your Quality Profiles

1. Click on the **Quality Profiles** menu.
2. Make sure you have selected the **Salesforce Lightning profile** as the default for both the Javascript and Visualforce & Lightning languages.  This can be done with the settings cog to the right of the profile name.

## Running a scan
There are few ways to run your scan. The first is using our **SFDX plugin** (this requires the [Salesforce CLI](https://developer.salesforce.com/tools/sfdxcli){target="_blank"} and the [SFDX CodeScan Plugin](https://www.npmjs.com/package/sfdx-codescan-plugin){target="_blank"} to be installed).  
:::(Info) (Note:)
This will not work behind a proxy currently. 
:::

1. Generate a **token** from the **My Account>Security** menu in SonarQube™.

2. Open a command prompt and navigate into: 
```
/runner/my-project
```
3. Run the following command:
```
sfdx codescan:run --token <token> --projectkey my-project-key --organization default-organization --server https://your.server.url
```
The organization key above will work for the Community edition of SonarQube™ but may need to be edited depending on your setup if using a paid edition.

You can also use **Ant** (this requires **Ant version 1.9+**).
:::(Info) (Note:)
You will need to edit **antbuild.properties** if your SonarQube™ installation is different than usual or if you have a proxy. You can also edit **/runner/antbuild.xml** if you want to customize your workflows.
:::
### SonarQube™ ant plugin
For more instructions on how to setup the **SonarQube™ ant plugin**, see [https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-ant/](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-ant/){target="_blank"} you should check the steps that the ant script takes are appropriate for your requirements.

1. Create a copy of the **sonar-project-template** folder in the runner directory of this folder and put it in the same project. Let’s call ***it /runner/my-project***.  Add the following to the ***sonar-project.properties*** file in the **my-project** folder.
2. Set ***sonar.login=*** to a token available from the **My Account>Security menu** in SonarQube™.
3. Set ***sonar.projectKey=myproject***
4. Set ***sonar.projectName=My Project***
5. Set ***salesforce.username***, ***salesforce.password*** and ***salesforce.url*** to your Salesforce **username/password**. Your Salesforce token also has to appended to the end of your salesforce.password parameter. 
**For example:** *salesforce.password=passwordtoken*. 
Setting your Salesforce username, password and url is not necessary if you want to analyse static content. Please use a system administrator user profile for this otherwise you may experience strange errors when downloading the code or executing tests.
* Open a command prompt and navigate into ***/runner/my-project***
* Run the following command:
```
ant -f ../antbuild.xml analyse
```
:::(Info) (Note:)
If the Anyone group is not granted Execute Analysis permission or if the SonarQube™ instance is secured (the **sonar.forceAuthentication property** is set to **true**), the credentials of a user having been granted Execute Analysis permission have to be provided through the **sonar.login** and **sonar.password properties**.
:::

## Proxies

* If your network has a proxy, you will need to pass some more parameters to avoid license errors.

* A guide for this is available [here](https://knowledgebase.autorabit.com/codescan/docs/setting-up-codescan-for-use-with-a-proxy){target="_blank"}.

## Having trouble?

* Read the tutorials
* Check the troubleshooting section
* Contact [support](https://www.codescan.io/contact/){target="_blank"}
