This document is a guide on how to add a Salesforce project to your CodeScan cloud account and run the analysis.

1.  Login into your CodeScan account.
2.  Once you login into your CodeScan account, on the top right corner, click on the (**+**) icon and select **Analyze new project**.
3.   It takes you to a different window. Choose the **Organization** for which you'd like to create a project.
4.  In the next window, click on **Add Analysis Project** option.
5.  You will now see a new popup window, select **Salesforce** from the given options.
6.  Next, choose the environment from the dropdown between **Production/Developer**, **My own domain**, and **Sandbox**. Click on **Authorize**.
7.  Once you click on Authorize it will redirect to the **Salesforce login** page. Validate your credentials and click on **Login**.
8.  Enter the necessary information in the below fields and then click on **Add and Run Now.**
    *   Enter the project version under **Default Project Version**
    *   Choose the **Unit Test Mode** from the dropdown options: _Run Unit Tests, Use Previous Run, Disabled_
    *   Now, enter the **project key** followed by the **project name**.
        
        Note:
        
        To know where to find the project key, refer to our document on how to do it by clicking [here](https://knowledgebase.autorabit.com/codescan/docs/how-to-find-a-project-key-in-codescan).
        
    *   Under **Scheduling**, choose whether you want to run the project automatically by selecting **Daily** or manually by selecting **Manual**.
    *   If you select **Daily**, another field named **Schedule** has to be selected by choosing the time you want the automatic analysis to be triggered.

This triggers the project analysis along with the project being added under your CodeScan organization.

### "ip restricted" error

If your scan fails with the IP restricted error, please refer to the [troubleshooting article](/codescan/docs/ip-restricted-issue).
