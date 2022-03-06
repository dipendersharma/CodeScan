## Metadata_Start
## title: CodeScan with Windows Agents
## original-url : https://knowledgebase.autorabit.com/docs/codescan-with-windows-agents
## article-id : 2298f828-de6e-461d-9285-b9e3b2d2f404
## seo-title : 
## description : 
## Metadata_End
## Requirements
You will need:

* Jenkins
* Salesforce CLI
* Git 

## Add Environment Variables

* In user environment Path variable, add the **SalesForce CLI** and **Git bin directories**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28346%29.png)
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28347%29.png){height="" width=""}

* In the System environment Path variable add the **Git\cmd**, **Git\usr\bin**, and **Salesforce CLI\bin directories**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28348%29.png)
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28349%29.png){height="" width=""}

## Setup Jenkins

1. In Jenkins, create a **[credential](https://docs.cloudbees.com/docs/cloudbees-ci/latest/cloud-secure-guide/injecting-secrets){target="_blank"}** containing your CodeScan token ([learn how to find this here](https://knowledgebase.autorabit.com/codescan/docs/generating-a-security-token){target="_blank"}).
2. Create a **new Pipeline**.
3. In the **Pipeline script** section you will need to paste in the code with the highlighted variables changed, these are:
    * Your ***credential_name*** should be the name of the credential you created.
    * ***my_project*** should be the project key you would like to assign to your project.
    * ***my_organization*** should be your Organization Key ([learn how to find this here](https://knowledgebase.autorabit.com/codescan/docs/finding-your-organization-key){target="_blank"}).
        * The ***--server=yourserveraddress*** flag is required for self hosted instances.

```
node {

    stage('Pull from Git') {

      git 'https://wherever.com/me/my-repo.git'

    }

    withCredentials([string(credentialsId: 'credential_name', variable: 'codescan_token')]) {
stage('CodeScan') {
sh '''
echo y|sfdx plugins:install sfdx-codescan-plugin
      sfdx codescan:run --token=$codescan_token --projectkey=my_project --organization=my_organization
  exit $?
'''       
}
}
}
```
4. Run the **pipeline**. If everything is set up correctly and your Quality Gate passes, you will be able to see you pipeline pass.
5. If your Quality Gate fails, you will see the error in the CodeScan stage of the build.
