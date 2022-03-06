## Metadata_Start
## title: CodeScan Integration with AutoRABIT
## original-url : https://knowledgebase.autorabit.com/docs/codescan-integration-with-autorabit
## article-id : 9c91359e-88bc-4bc1-b603-8abbac5a8c92
## seo-title : CodeScan Integration with AutoRABIT | CodeScan Static Code Analysis
## description : AutoRABIT is a complete DevOps solution built for Salesforce. Learn more about integrating CodeScan static code analysis solutions into this environment.
## Metadata_End
AutoRABIT, an automated Release Management solution built for the Salesforce platform, delivers fast CI/CD solutions for DevOps teams.

This helps us to offer essential solutions to the [Salesforce DevOps](https://www.autorabit.com/blog/how-do-i-choose-the-best-salesforce-devops-tools/){target="_blank"} ecosystem. [AutoRABIT’s release management solution](https://www.autorabit.com/products/automated-release-management/){target="_blank"} partnered with our CodeScan automated code review and standardization enables developers on the Salesforce platform to deliver new customer experiences with better quality, greater velocity, and increased security.

To integrate all the functionalities included in your CodeScan account with AutoRABIT, you need to integrate CodeScan as a plugin with your AutoRABIT account which involves a few steps in your CodeScan as well as AutoRabit account.

To integrate [CodeScan](https://www.codescan.io/){target="_blank"} with the AutoRABIT, follow the prcodure as described below.

### Create a CodeScan Token


1. Click [here](https://knowledgebase.autorabit.com/codescan/docs/generating-a-security-token){target="_blank"} to see the documentation on how to create a security token.

2. Copy the **token**. This token will be used while storing your credential with [AutoRABIT](https://www.autorabit.com/){target="_blank"}.

### Store your CodeScan's credential in AutoRABIT

1. Login into your AutoRABIT account.

2. Go to the **Admin** module and click on **Credentials**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28305%29.png){height="" width=""}

3. Next, click on **Create Credential** from the right navigation bar.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28306%29.png){height="" width=""}

4. On the next pop up screen, give a **Credential name**.
5. Choose the Credential Type as **User name with Password**.
6. Choose your Credential Scope,
    * **Global:** Credential can be accessed within the team
    * **Private:** Credential for private usage

7. **Username**: Enter the username for your CodeScan account
8. **Password:** Use the copied token (CodeScan token) you made in the previous step as a password
9. Please double check that you use your CodeScan username instead of the email address that you use to log in to CodeScan.
10. Click **Save**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28307%29.png){height="" width=""}

### Integrate AutoRABIT with CodeScan

1. Go to **Admin > My Account** section.

2. Go to the **Plugins** section.
3. Select the **CodeScan/Lint** checkbox under **Static Code Analysis**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28308%29.png){height="" width=""}

4. Fill in the below details:
    * Enter the CodeScan hosted URL.
    *  For CodeScan cloud version use [https://app.codescan.io](https://app.codescan.io){target="_blank"}.
    * Choose the **Host Type** i.e., Cloud or On-premise. For CodeScan hosted on Cloud, you need to add the **Organization Key**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28309%29.png){height="" width=""}

5. Select your **Credential** from the drop-down.
6. Click **Test Connection** (![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28310%29.png)) iocn to check if the connection has been authenticated or not. A success message is displayed, after the authentication is completed.
7. Click **Save**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28311%29.png){height="" width=""}

8. Click on **Save** once again and you are all set with CodeScan integration.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28312%29.png){height="" width=""}
 

### Configuring CodeScan's Global Criteria

1. Go to **Admin > My Account** section.
2. Next, navigate to the **Validation Criteria-Static Code Analysis** section.
3. Select the **Enable** checkbox.
4. Enable the **CodeScan** checkbox and assign the Quality Gate status for all your projects. By default, it is set to **ERROR**, however, you can choose the criteria of your own. If the Quality Gate matches with the status assigned to the projects on your CodeScan tool, the validation process gets failed and the build aborts.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28313%29.png){height="" width=""}

5. Click **Save**.
6. Next, go to section **Commit Validation - Approval Settings**. In this section, you can allow CodeScan tools to identify potential software quality issues before the code moves to production and abort the commit process if the Quality Gate set earlier matches with the status in CodeScan application.
7. Select the checkbox: **Enable criteria based Review Process**
8. Enable the **Should pass validation criteria for Static Code Analysis** checkbox and then select the below checkboxes:
    * CodeScan
    * Auto reject commit process if the criteria are not met
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28314%29.png){height="" width=""}

9. Click **Save**.
10. Similar to CodeScan criteria globally configured in AutoRABIT for Commit operation, you can even set the same for Merge Process.
11. Go to next section: **Merge Settings**
12. Select the **Enable criteria based Review Process** checkbox.
13. Under **Should pass validation criteria for Static Code Analysis**, select the **CodeScan** checkbox.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28315%29.png){height="" width=""}

14. Now, click on **Save**.

## Running CodeScan SCA in AutoRABIT

After integrating AutoRABIT with CodeScan plugin, select **CodeScan** as Static Code Analysis tool to detect bugs, code smells and security vulnerabilities before the code moves to the production on AutoRABIT.


### During Deployment Process:

1. On the Deployment Settings screen, choose **CodeScan/Lint** as a **SCA tool**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28316%29.png){height="" width=""}

2. AutoRABIT has a provision for you to freeze or stop the deployment if the build doesn't meet the global criteria set under **My Account > Validation Criteria-Static Code Analysis settings** .
3. Select the **recipients** for the SCA alerts. To do so, enter the **recipient's email address** who all be notified about the alert in SCA Mail Notification field.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28317%29.png){height="" width=""}

4. Once the deployment is done, you can find the detailed **SCA Report** for the deployment process under **Deployment History**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28318%29.png){height="" width=""}

### During Merge Process:

While merging Salesforce records between two Version Control branches, you can allow CodeScan to check for any bugs, code smells and security vulnerabilities.

1. In the New Merge screen, go to the **Prevalidate Merge** section.

2. Select **CodeScan/Lint** as a **SCA tool**.
3. To run CodeScan on all of the **Apex Classes, Triggers, Apex Pages & AuraDefinitionBundles**, select the checkbox highlighted in the red box below.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28319%29.png){height="" width=""}

4. Proceed ahead with the Merge process.
5. Find the detailed **SCA Report** under **Commits** screen.

### During Commit Process:

While performing a validation deployment before actually committing the changes, you can allow CodeScan to check for any bugs, code smells and security vulnerabilities.

1. In the Submit for Validation screen, go to the **Validation Reports** section.

2. Select **CodeScan/Lint** as a **SCA tool**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28320%29.png){height="" width=""}

3. Here, you will have provision to set the condition for running CodeScan SCA tool, i.e, running for all the **Apex Classes, Triggers, Apex Pages & AuraDefinitionBundles** components or stating the time period from where it will run.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28321%29.png){height="" width=""}
 
4. Proceed ahead with the Prevalidate Commit process.
5. Find the detailed **SCA Report** under **Commits** screen.

### During CI Job:

While carrying out the CI Job process, you can configure CodeScan to check for any bugs, code smells and security vulnerabilities.

1. In the Create CI Job screen, search for the **Run Code Analysis Report** checkbox under the **Build** section.

    * Enable the checkbox: **Run Code Analysis Report**.
    * Select **CodeScan/Lint** as a **SCA tool**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28322%29.png){height="" width=""}

 2. Here, you will have provision to set the condition for running CodeScan SCA tool, i.e, running for all the **Apex Classes, Triggers, Apex Pages & AuraDefinitionBundles** components or from the full source or stating the time period from where it will run.
3. Also, you can set the priority, which means if the priority set is not achieved, the current build is unstable.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28323%29.png){height="" width=""}

4. Find the detailed **SCA report** in CI Job Results screen under Build Details section.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28324%29.png){height="" width=""}


### CodeScan SCA Results:


During the implementation phase of a Security Development Lifecycle (SDL), [Static Code Analysis](https://www.autorabit.com/products/codescan/){target="_blank"} is usually performed as part of a Code Review.

* CodeScan being a Static Analysis tool continuously detects and reports on data flow problems, software defects, language implementation errors, inconsistencies, dangerous usage, coding standard violations, and security vulnerabilities.

* AutoRABIT generates a detailed SCA Result report and the Lint runs by default every time you run a [static code analysis](https://knowledgebase.autorabit.com/docs/static-code-analysis). Lint analyzes source code to flag programming errors, bugs, stylistic errors, and suspicious constructs.

* Lint Report will only display information about AuraBundle components.

These reports will have information about the files that were reviewed and its related violations.

* Click on each file to view its related violations that will appear at the bottom right side of the page.

* If you click on any violation, it will take you to the respective line (in the black screen on the right side) where such violation occurred.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28325%29.png){height="" width=""}

* Click on the **link** at the bottom of the page as in the image below which will redirect you to CodeScan Analysis Dashboard page to compare the SCA report in your CodeScan account.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28326%29.png){height="" width=""}
