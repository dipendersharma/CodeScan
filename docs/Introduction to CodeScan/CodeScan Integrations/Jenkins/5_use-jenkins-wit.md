## Metadata_Start
## title: Use Jenkins with CodeScan Salesforce project
## original-url : https://knowledgebase.autorabit.com/docs/use-jenkins-with-codescan-salesforce-project
## article-id : 9c30a617-3354-4bd1-9d56-0f5abc33bffa
## seo-title : CodeScan Integrations | Use Jenkins with CodeScan Salesforce project
## description : Here is the step by step process to create a Jenkins project with CodeScan.
## Metadata_End
The following is a guide to setting up Jenkins for use with CodeScan. It assumes that:

* You have **Jenkins** installed.
* You have the **Ant** and **Git plugins** for Jenkins installed.

## Creating a Jenkins Project to use with [CodeScan](https://www.codescan.io/)

* Create a **new Freestyle project**.

* Add a **String parameter**:

    * Name it ***sonar.projectVersion***
    * Make the default value ***1***

* Add another **string parameter**:

    * Name it ***salesforce.username***
    * Make the default value your Saleforce username eg. **will@example.com**

* Add a **password parameter**:

    * Name it ***salesforce.password***
    * Make the default value your Salesforce password + your Salesforce token eg. **passwordtoken**

* Add another **string parameter**:

    * Name it ***salesforce.url***
    * Make the default value [https://login.salesforce.com](https://login.salesforce.com){target="_blank"} to pull from your production instance or [https://test.salesforce.com/](https://test.salesforce.com/){target="_blank"} to pull from your sandbox instance

* Add another **string parameter**:

    * Name it ***sonar.projectKey***
    * Make the default value ***project1***

* Add another **string parameter**:

    * Name it ***sonar.projectName***
    * Make the default value whatever you like. This will be the name displayed in SonarQube™.

* Add another **string parameter**:

    * Name it ***sonar.host.url***
    * Make the default value the url of your SonarQube™ instance. The default for SonarQube™ running locally would be **http://localhost:9000**

* In the build section of the configuration click **Add Build Step > Invoke Ant**.

    * In the targets section write ***deletesrc download***.
    * In the Build File section, fill in the path to the ***antbuild.xml*** file in the runner folder of your CodeScan installation. eg. ***C:/great-tools/sonar-salesforce-plugin3.x/runner/antbuild.xml***
    * In the Properties section, type ***user.dir=${WORKSPACE}***
    * Leave the Java options blank.

* Add another **Invoke Ant step**:

    * In the targets section write ***sonar***.
    * In the Build File section, fill in the path to the ***antbuild.xml*** file in the runner folder of your CodeScan installation. eg. ***C:/great-tools/sonar-salesforce-plugin3.x/runner/antbuild.xml***
    * In the Properties section, type ***user.dir=${WORKSPACE}***
    * In the java options add the path to your temp directory. eg. **-Djava.io.tmpdir=C:\Users\some-guy\AppData\Local\Temp**\
    * You can also add ***-Xmx1024m*** to the end of the Java options field to assign memory.

Save the **project** and click **Build with Parameters**. The results will be available in SonarQube™.
