This document is a guide on how to add a GitLab project to your CodeScan cloud account and run the analysis.

1.  Login to your CodeScan account.
2.  Once you login into your [CodeScan](https://www.codescan.io/) account, on the top right corner, click on the (**+**) icon and then select **Analyze new project**.
3.   It takes you to a different window. Choose the **Organization** for which you'd like to create a project. Click on **Set Up**.
4.  In the next screen, click on **Add Analysis Project** button. 
5.  You will now see a new popup window, click on [**GitLab**](https://knowledgebase.autorabit.com/codescan/docs/integrating-codescan-in-gitlab) from the given options.
6.  Now another popup window appears with the fields: **Choose a repository**, **Project Branch**, **Check Pull Requests**, **Key**, and **Name**
    *   Choose the repository you want to add followed by the project branch name.
    *   Make sure you select the checkbox under **Check Pull Requests**, this will add **webhooks**.
    *   Now, enter the **project key** followed by the **project name**.  
        
        Note:
        
        To know where to find the project key, refer to our document on how to do it by clicking [here](https://knowledgebase.autorabit.com/codescan/docs/how-to-find-a-project-key-in-codescan).
        
    *   Once you fill out all the details in the popup window, click on **Add and Run Now**.
7.  This triggers the project analysis along with the project being added under your CodeScan organization.
8.  You can view the project analysis report by clicking on **Details** from your VC repository.
9.   When you click the link, it will take you to the CodeScan Project page, where you can view your project's log report. Now that the web-hooks have been created, every time there is a push or pull request made to the tracked branch, an analysis will be triggered in CodeScan.
