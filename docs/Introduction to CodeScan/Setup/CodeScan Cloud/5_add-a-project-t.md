This document is a guide on how to add a git project to your CodeScan cloud account and run the analysis.  
This method can be used to add a project from any git based SCM however if you are using a cloud version of GitHub, Bitbucket or GitLab, we suggest you use the specific integration for your repository.

1.  Login to your CodeScan account.
2.  Once you login into your CodeScan account, on the top right corner, click on the (**+**) icon and select **Analyze new project**.
3.   It takes you to a different window. Choose the **Organization** for which you'd like to create a project.
4.  In the next screen, click on **Add Analysis Project** option.
5.  You will now see a new popup window, select **git** from the given options.
6.  Enter the necessary information in the below fields and then click on **Add and Run Now.**
    *   Enter the repository details such as **URL**, **username,** and **password** in their respective fields followed by the **project branch** name.
    *   Now, enter the **project key** followed by the **project name**.  
        
        Note:
        
        To know where to find the project key, refer to our document on how to do it by clicking [here](https://knowledgebase.autorabit.com/codescan/docs/how-to-find-a-project-key-in-codescan).
        
    *   Under **Scheduling**, choose whether you want to run the project automatically by selecting **Daily** or manually by selecting **Manual**.
    *   If you select **Daily**, another field named **Schedule** has to be selected by choosing the time you want the automatic analysis to be triggered.

This triggers the project analysis along with the project being added under your [CodeScan](https://www.codescan.io/) organization.

This project will now run daily at the scheduled time unless configured otherwise.
