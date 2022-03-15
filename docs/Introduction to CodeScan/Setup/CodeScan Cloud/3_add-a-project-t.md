This document is a guide on how to add a GitHub project to your CodeScan cloud account and run the analysis.

1.  Login into your CodeScan account.
2.  Once you login into your CodeScan account, on the top right corner, click on the '**+**' icon and select **Analyze new project**.  
    ![Analyze New Project](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-1635045365564.png)
3.  It takes you to a different window. Choose the **Organization** for which you'd like to create a project. ![Analyze Projects](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-1635045425810.png)
4.  In the next window, click on **Add Analysis Project** option.![Add Analysis Project](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-1635045455803.png)
5.  You will now see a new popup window, select [**GitHub**](https://knowledgebase.autorabit.com/codescan/docs/integrating-codescan-with-github-actions) from the given option.![Add New Project](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-1635045811458.png)
6.   Once you select [GitHub](https://knowledgebase.autorabit.com/codescan/docs/github-actions) it will redirect to the **GitHub** **login** page. Validate your credentials and click on **Login**.![GitHub Login](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-1635045572121.png)
7.  Enter the necessary information in the below fields and then click on **Add and Run Now**.![Add and Run Now](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-1635045694536.png)
    *   Choose the repository you want to add followed by the **Project Branch** name.
    *   Make sure you select the checkbox under **Check Pull Requests**.
    *   Now, enter the **project key** followed by the **project name**.  
        
        Note:
        
        To know where to find the project key, refer to our document on how to do it by clicking [here](https://knowledgebase.autorabit.com/codescan/docs/how-to-find-a-project-key-in-codescan).
        
8.  This triggers the project analysis along with the project being added under your [CodeScan](https://www.codescan.io/) organization.
9.   You can view the project analysis report by clicking on **Details** from your VC repository.![VC repository](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-1642586013379.png)
10.   When you click the link, it will take you to the CodeScan Project page, where you can view your project's log report.![CodeScan Project page](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-1642590860205.png)

Now that the webhooks have been created, every time there is a push to the tracked branch or pull request made/updated against the tracked branch, an analysis will be triggered in CodeScan.
