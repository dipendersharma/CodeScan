## Metadata_Start
## title: Integrating CodeScan with Github Actions
## original-url : https://knowledgebase.autorabit.com/docs/integrating-codescan-with-github-actions
## article-id : 28457c61-f0b0-410b-adc0-56c224ec4ab9
## seo-title : 
## description : 
## Metadata_End
You can now run CodeScan static code analysis jobs from Github workflow. The codescan action will produce a **SARIF report file** with the analysis result.

There are only a few lines to add to your **.YML file** for codescan to be triggered.

First, we'll need to add your CodeScan token as a variable we can access in our **.YML file**.

* Open your project and navigate to **Repository Settings>Secrets>Add new secret**.
* Add your token with the name **codescan_token** and check the **Secured** box. To learn how to generate a token, see [here](https://knowledgebase.autorabit.com/codescan/docs/generating-a-security-token){target="_blank"}. 

Now you'll be able to access this variable by using **$codescan_token** in your **.YML file**.
 
If you do not have a workflow setup on your GitHub Repository, go to **Actions > New workflow** to create a **.yml workflow**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28340%29.png){height="" width=""}

Add the following into your **.YML file** in the workflow: 

```
name:
  CI
  on:
    push:
      branches: [main]
    pull_request:
      branches: [main]
  jobs:
    build:
      runs-on: ubuntu-latest
      steps:
        - name: Checkout repository
          uses: actions/checkout@v2
        - name: Cache files
          uses: actions/cache@v2
          with:
              path: |
                  ~/.sonar
              key: ${{ runner.os }}-sonar
              restore-keys: ${{ runner.os }}-sonar
        - name: Run Codescan On Push
          if: github.event_name == 'push'
          uses: codescan-io/codescan-scanner-action@1.2
          with:
            organization: ‘Enter organization key here’
            projectKey: ‘Enter project key here’       
            login: ${{ secrets.codescan_token }}
        - name: Run Codescan On PR
          if: github.event_name == 'pull_request'
          uses: codescan-io/codescan-scanner-action@1.2
          with:
            organization: ‘Enter organization key here’
            projectKey: ‘Enter project key here’
            login: ${{ secrets.codescan_token }}
            args: |
              sonar.branch.name=${{github.head_ref}}
              sonar.branch.target=${{github.base_ref}}
              sonar.branch.type=SHORT
        - name: Upload SARIF file
          uses: github/codeql-action/upload-sarif@v1
          with:
            sarif_file: codescan.sarif
```
You will need to replace the placeholder variables (in **bold**) in the env section of the script with your **Project Key** and **Organization Key**.

Now, you will be able to view the **.yml workflow** on your Repository.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28341%29.png){height="" width=""}

And also check for the name of the master branch on both CodeScan platform and Git repository, as the new Git update changed the name of master branch to main.

If the name on CodeScan platform is not the same as Git Repository, go to your **CodeScan project** and then navigate to **Dashboard> Administration> Branches & Pull Requests> Actions** and change the branch name.

The branches names and types are set by the following parameters:
* **sonar.branch.type**: this is SHORT or LONG as described in the [Branching Article](https://knowledgebase.autorabit.com/codescan/docs/understanding-branches-in-codescan-cloud){target="_blank"}
* **sonar.branch.target**: the comparison branch for SHORT type branches
* **sonar.branch.name**: the name of the branch

The **upload SARIF file**  in the **.yml** helps you to get the code analysis reports in two ways:

1. For the files already existing in the repository, results can be found under code scanning alerts under the **Security** tab on GitHuB repository.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28343%29.png){height="" width=""}

2. For the new files being uploaded to the repository, you can view the analysis during the pull-requests on GitHub by clicking on the details:
    * Select the relevant pull-request and then click on **Details**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28344%29.png){height="" width=""}

    * Once you click on the **Details**, go to **Code scanning results > CodeScan**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28345%29.png){height="" width=""}

    * Results are categorized as follows:

        * All the **Bugs** and **Vulnerabilities** are marked as **ERRORS**.
        * Whereas, all the major and minor **Code Smells** are marked as **WARNINGS**.

This **.yml file** helps you to run an analysis on the project while linking it to CodeScan.

You can go to the **CI workflow** under **Git actions** to view the analysis.
