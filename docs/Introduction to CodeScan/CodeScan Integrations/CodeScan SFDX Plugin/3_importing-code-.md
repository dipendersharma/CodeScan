## Metadata_Start
## title: Importing Code Coverage from SFDX projects
## original-url : https://knowledgebase.autorabit.com/docs/importing-code-coverage-from-sfdx-projects
## article-id : 528bc3b7-e665-43b6-8dff-dfb34f917f30
## seo-title : 
## description : 
## Metadata_End
CodeScan now provides a way to view your unit test coverage from your SFDX projects in SonarQube™.

## Requirements

* A working **SonarQube™ (7.9+)** installation
* A licensed **CodeScan (4.1+) plugin**
* An **SFDX** project linked to your Salesforce Org

## Configuration

Run your tests in your org using ***sfdx force:apex:test:run*** and the following parameters:

* ***-c*** This is to return code coverage
* ***-d .*** This is to define the output directory. In this case the current directory (.).
* ***-u your-username*** This is the username or alias of the org you would like to run tests in.
* ***-r json*** This defines the output type as a JSON file.

The end command should look something like as below, run this command:
```
sfdx force:apex:test:run -c -d . -u username -r json
```

If all goes with the plan, you should find a **JSON file** in your project’s directory named this as ***test-result-TESTRUNID.json*** where ***TESTRUNID*** is the ID of your test run.

In order to import this into **SonarQube™**, pass the parameter ***sf.testfile*** with your build. 
For the file you have just created in the root folder of your project, you will need to pass ***sf.testfile=test-result-TESTRUNID.json***.

If you have created the test file somewhere else, you will need to provide the path relative to the root folder of your project.
