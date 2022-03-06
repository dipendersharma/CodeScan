## Metadata_Start
## title: Integrating CodeScan in GitLab
## original-url : https://knowledgebase.autorabit.com/docs/integrating-codescan-in-gitlab
## article-id : ec75d7be-5f37-4862-bd3a-8b358baa048b
## seo-title : GitLab Integration With CodeScan
## description : Properly configuring the Gitlab integration for your CodeScan tool will help you see the greatest benefits from utilizing it in your Salesforce DevOps pipeline.
## Metadata_End
Integrating CodeScan into your GitLab pipeline is easy with our sfdx plugin. There are only a few lines to add to your **.YML file** to run codescan when a build is triggered.

 :::(Info) (Note:)
The following is based on a docker pipeline with **Java** and **Node** installed in the container. 
:::

First, we'll need to add your CodeScan token as a variable we can access in our **.YML file**.

* Open your project and navigate to **Settings>CI/CD** then expend the Variables section.
* Add your token with the name **CODESCAN_TOKEN** and check the masked variable box. To learn how to generate a token, see [here](https://knowledgebase.autorabit.com/codescan/docs/generating-a-security-token){target="_blank"}. 

Now you'll be able to access this variable by using **$CODESCAN_TOKEN** in your **.YML file**.

Add the following into your **.YML file**: 

:::(Info) (Note:)
The following is a great way to get started scanning with this plugin, however this script will install the Salesforce CLI and [CodeScan plugin](https://www.codescan.io/products/editor-plugins/){target="_blank"} with each run. A better implementation would include these installations in the docker image used.
:::

```
image: joeferner/node-java

stages:
 - codescan

scan:
 stage: codescan
 script:
  - mkdir /tmp/sfdx
  - wget -q https://developer.salesforce.com/media/salesforce-cli/sfdx-linux-amd64.tar.xz -O /tmp/sfdx/sfdx-linux-amd64.tar.xz
  - tar xJf /tmp/sfdx/sfdx-linux-amd64.tar.xz -C /tmp/sfdx/ --strip-components 1 
  - /tmp/sfdx/install
  - echo y|sfdx plugins:install sfdx-codescan-plugin
  - sfdx codescan:run --token=$CODESCAN_TOKEN --projectkey=your_project_key --organization=your_organization_key -Dsonar.branch.name=$CI_COMMIT_REF_NAME -Dsonar.branch.target=$CI_EXTERNAL_PULL_REQUEST_TARGET_BRANCH_NAME
```

You will need to replace the placeholder variables (in **bold**) in the env section of the script with your **Project Key** and **Organization Key**.

The branches names and types can be set by the following parameters:
* **sonar.branch.type**: this is SHORT or LONG as described in the [Branching Article](https://knowledgebase.autorabit.com/codescan/docs/understanding-branches-in-codescan-cloud){target="_blank"}
* **sonar.branch.target**: the comparison branch for SHORT type branches
* **sonar.branch.name**: the name of the branch

By default, the CodeScan SFDX plugin will fail if the Quality Gate fails. If you would prefer that the build passes despite the quality gate, use the **--nofail** tag when calling **sfdx codescan:run**.

You can find a complete list of flags and examples on our [npm plugin page](https://www.npmjs.com/package/sfdx-codescan-plugin){target="_blank"}.
