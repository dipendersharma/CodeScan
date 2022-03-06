## Metadata_Start
## title: Jenkins: java.lang.OutOfMemoryError: Java heap space
## original-url : https://knowledgebase.autorabit.com/docs/jenkins-javalangoutofmemoryerror-java-heap-space
## article-id : 449de5c4-b44f-4c12-9b4d-bc9f71bc9f7c
## seo-title : Jenkins integrations | Jenkins: java.lang.OutOfMemoryError
## description : CodeScan by AutoRABIT is a static code analysis solution for Salesforce DevOps teams. Visit here to learn how to address common issues with Jenkins.
## Metadata_End
This error can be solved by manually adding a parameter to dedicate memory to the build process.

* In your Jenkins project, click **configure**.
* Scroll down to the **Build** section of the page to the Build Step titled **Invoke Ant** with the fields:
    * **Ant Version**: [CodeScan](https://www.codescan.io/) Bundled Ant
    * **Targets**: sonar

* Click on **Advanced**.
* In the **Java Options** field, add the parameter -**Xmx2000m**. This will assign **2000mb** of memory to you build.

If after increasing the heap space you get the error: 

```
Error occurred during initialization of VM Could not reserve enough space for xxxxxxKB object heap
```

The problem may be that you are using a **32 bit version of Java**.  Please see this [article](https://knowledgebase.autorabit.com/codescan/docs/error-occurred-during-initialization-of-vm-could-not-reserve-enough-space-for-xxxkb-object-heap){target="_blank"} for more details.
