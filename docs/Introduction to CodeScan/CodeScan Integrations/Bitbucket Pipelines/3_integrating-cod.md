## Metadata_Start
## title: Integrating CodeScan in Bitbucket Pipelines
## original-url : https://knowledgebase.autorabit.com/docs/integrating-codescan-in-bitbucket-pipelines
## article-id : ddea54e9-0698-41dc-ba3e-5db9596a1a7d
## seo-title : Integrating CodeScan in Bitbucket Pipelines
## description : Integrating CodeScan into your Bitbucket pipeline is easy with our SFDX plugin. Visit here to learn more about how to perform and utilize this integration.
## Metadata_End
Integrating CodeScan into your Bitbucket pipeline is easy with our sfdx plugin. There are only a few lines to add to your **.YML file** to run CodeScan when a build is triggered.

:::(Info) (Note:)
The following is based on a docker pipeline with **Java** and **Node** installed in the container.  
:::

First, we'll need to add your [CodeScan](https://www.codescan.io/){target="_blank"} token as a variable we can access in our **.YML file**.

* Open your project and navigate to **Repository Settings > Repository Variables** (you'll find this under Pipelines).
* Add your token with the name **codescan_token** and check the **Secured** box. To learn how to generate a token, see [here](https://knowledgebase.autorabit.com/codescan/docs/generating-a-security-token){target="_blank"}. 
* Now you'll be able to access this variable by using **$codescan_token** in your **.YML file**.

Add the following into your **.YML file**: 
:::(Info) (Note:)
The install scripts for the sfdx plugin have been added to the steps below to provide easy boiler plate code. This installation should be completed in the container in a production pipeline. 
:::

```
image: joeferner/node-java #Your docker image, complete with node and java (8+) installed.
pipelines:
  pull-requests:
    'master': #The destination branch of the pull requests we’ll be checking
    - step:
        caches:
          - node
        script:
          - mkdir /tmp/sfdx
          - wget -q https://developer.salesforce.com/media/salesforce-cli/sfdx-linux-amd64.tar.xz -O /tmp/sfdx/sfdx-linux-amd64.tar.xz
          - tar xJf /tmp/sfdx/sfdx-linux-amd64.tar.xz -C /tmp/sfdx/ --strip-components 1 
          - /tmp/sfdx/install
          - echo y|sfdx plugins:install sfdx-codescan-plugin
          - sfdx codescan:run --token=$codescan_token --projectkey=project1 --organization=<your CodeScan Cloud Organisation key> -Dsonar.pullrequest.key=$BITBUCKET_PR_ID -Dsonar.pullrequest.branch=$BITBUCKET_BRANCH -Dsonar.pullrequest.base=$BITBUCKET_PR_DESTINATION_BRANCH -Dsonar.scm.provider=git
  branches:
    'master': #The branch of the project we’ll be tracking the history of
    - step:
        caches:
          - node
        script:
          - mkdir /tmp/sfdx
          - wget -q https://developer.salesforce.com/media/salesforce-cli/sfdx-linux-amd64.tar.xz -O /tmp/sfdx/sfdx-linux-amd64.tar.xz
          - tar xJf /tmp/sfdx/sfdx-linux-amd64.tar.xz -C /tmp/sfdx/ --strip-components 1 
          - /tmp/sfdx/install
          - echo y|sfdx plugins:install sfdx-codescan-plugin
          - sfdx codescan:run --token=$codescan_token --projectkey=<project1 --organization=<your CodeScan Cloud Organisation key> -Dsonar.branch.name=$BITBUCKET_BRANCH -Dsonar.scm.provider=git

```

You will need to replace the placeholder variables (in **bold**) in the script with your **Organization Key**.

The pull request names keys are set by the following parameters:

* **sonar.pullrequest.key**: this is the PR number.
* **sonar.pullrequest.branch**: the name of the branch.
* **sonar.pullrequest.base**: the destination branch of the PR.  This also determines where the comparison is made in the CodeScan project.

By managing the conditionals in your script that determines what triggered the build and defining the branch type, name, and target using [Bitbucket pipeline's built in variables](https://support.atlassian.com/bitbucket-cloud/docs/variables-and-secrets/){target="_blank"}, you can create a project that gives you visibility on your new code while allowing you to plan your refactoring effort.

By default, the CodeScan SFDX plugin will fail if the Quality Gate fails. If you would prefer that the build passes despite the quality gate, use the **--nofail** tag when calling **sfdx codescan:run**.

You can find a complete list of flags and examples on our [npm plugin page](https://www.npmjs.com/package/sfdx-codescan-plugin){target="_blank"}.
