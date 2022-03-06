## Metadata_Start
## title: Understanding branches in CodeScan Cloud
## original-url : https://knowledgebase.autorabit.com/docs/understanding-branches-in-codescan-cloud
## article-id : 5e55ad76-1411-42b5-a8c7-d1fd08c19e3f
## seo-title : 
## description : 
## Metadata_End
Branches allow you to keep track of changes that may affect the branch that your project is linked to. There are two types of branches:

1. **Long lived branches**: which allow you to see the full dashboard and history of your project.
2. **Short lived branches**: which allow you to the the delta in issues between your branch and your master/production/target.

### GitHub and Bitbucket
When creating an Analysis Project from a GitHub or Bitbucket repository in CodeScanCloud, you will be asked to choose the branch that the project is linked to. This branch will become your Main Branch. If you also selected Check Pull requests, any changes that affect this main branch will be reflected in this project with the branch functionality.

### Pull Requests
If you have set your Main Branch to master, any relevant pull request will be analysed when it is created and every time it is updated. The results will be displayed in the same page as your Main Branch analysis under the branches drop down menu.

### Visual Studio Team Services (VSTS)
When a pull request is created in a VSTS repository or in a repository tracked by your VSTS Build Definition, a new branch will be created on your CodeScan Cloud project. Please note that any remote repositories will have to have Continuous Integration and Pull Request Validation checked for the appropriate branches in the Build Definition’s Triggers menu.

### Salesforce
When creating an Analysis Project from Salesforce, the Org or Sandbox you authorize when creating the project will become your master. Sandboxes can be added to this project as **branches** by editing the project from the Project Analysis page. This allows for easy comparison between Production Orgs or Sandboxes, and is especially good for checking features before going into production.

### Comparing Branches
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28157%29.png){height="" width=""}

Here you can see the branch has 4 new violations. If the branch is selected, the details of the violation/s can be seen. All new branches that are added in this way will be deleted in **30 days** if they are not analysed again.

### Managing branches

1. In your Project Analysis page, go to **Project Setting > Branches and Pull requests**. This page allows users to delete any new branches and also change the branch that the Analysis Project is checking.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28218%29.png){height="" width=""}

    * **Delete Branch**: To delete a branch, click the(![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28224%29.png)) button next to the branch and click **Delete Branch**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28220%29.png){height="" width=""}

    * **Rename Branch**: To change the branch that the Analysis Project is tracking, click the (![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28223%29.png)) icon next to the main branch and click **Rename Branch**. Enter the name of the branch you would like to begin tracking. Changes will only be reflected on the project’s Overview page once the analysis has been performed again.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28219%29.png){height="" width=""}


If you have any further questions about CodeScan Cloud, please [contact us](https://www.codescan.io/contact/){target="_blank"}.
