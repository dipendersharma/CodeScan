## Metadata_Start
## title: CodeScan and Flosum Integration
## original-url : https://knowledgebase.autorabit.com/docs/codescan-and-flosum-integration
## article-id : 03176b14-b026-4489-935a-399070d7ca9f
## seo-title : CodeScan and Flosum Integration
## description : CodeScan works alongside Flosum for Salesforce release management. Visit here for specifics on how these technologies integrate with each other for DevOps.
## Metadata_End
**Flosum** is a release management tool for the Salesforce platform. Flosum users can now integrate CodeScan in their deployments to achieve error-free and secure releases.

1. First, install the **CodeScan package** in your **Flosum org**. Package URL needs to be given by customer success manager.

2. After installation, click on **App launcher** and open **Flosum-Codescan**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28327%29.png){height="" width=""}

3. There are few settings which we need to enable in Flosum-CodeScan Package.

    * **Activate CodeScan:** Click on **Activation** tab **Enable Synchronization** for Flosum-CodeScan.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28328%29.png){height="" width=""}

    * **Authorize CodeScan:** In order to authenticate codeScan account you need to have an **organization key** as well as **access token** from CodeScan Server.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28329%29.png){height="" width=""}

    * **Select Component Types:** We support six metadata components as shown in the below image and you have to select the branch in order to do perform static code analysis. So, you have to select a **branch** and click on **Save**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28330%29.png){height="" width=""}

    * **Create new project from existing branch:** You can select an existing Flosum branch and click on **Create** button to create a new project in CodeScan which you can analyze.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28331%29.png){height="" width=""}

Now you have done your complete setup with respect to Flosum-CodeScan


## How Does Flosum-CodeScan Work

### Case 1: Create a new branch and add all metadata components

In this use case we will create a new branch in Flosum and add all new metadata components and do a [static code analysis](https://www.codescan.io/){target="_blank"} on a CodeScan server.


1. Go to **Flosum**, Create the **new branch** and attach it to existing repository and click on **save**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28332%29.png){height="" width=""}

2. Now go to **Flosum-CodeScan Package**, click on **component type** and select all the component types and associate branch and click **save**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28333%29.png){height="" width=""}


3. Login to [app.codescan.io](http://app.codescan.io){target="_blank"} using your credentials and you will notice that the branch is populated in the CodeScan Server with your Project.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28334%29.png){height="" width=""}


4. Select the **branch** and click on a button **attach analysis project** and attach it as a Webhook.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28335%29.png)
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28336%29.png){height="" width=""}

5. Now you deploy metadata components like **Apex Class**, **triggers** to your branch and CodeScan will trigger static code analysis on the fly.


### Case 2: For an existing branch create a new project

In this use case we will authorize existing branch in Flosum and add all new metadata components and do a static code analysis on a CodeScan server.

:::(Info) (Note:)
This case is very similar to case 1, only step 1 is added as an extra functionality.
:::


1. Go to **Flosum-CodeScan Package** and Click on **Create project** from a branch, select the **branch** and click on **create**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28337%29.png){height="" width=""}

2. Click on **component type** and select all the component types and associate branch and click **save**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28338%29.png){height="" width=""}


3. Login to [app.codescan.io](http://app.codescan.io){target="_blank"} using your credentials and you will notice that the branch is populated in the CodeScan Server.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28339%29.png){height="" width=""}

4. Click on the **branch** and attach analysis as webHook.

5. Now you deploy [metadata](https://www.autorabit.com/blog/the-role-of-metadata-in-devops-for-salesforce/){target="_blank"} components like **Apex Class**, **triggers** to your branch and CodeScan will trigger static code analysis on the fly.

:::(Info) (Note:)
Step 3, 4, and 5 have similar functionality as Case 1.
:::
