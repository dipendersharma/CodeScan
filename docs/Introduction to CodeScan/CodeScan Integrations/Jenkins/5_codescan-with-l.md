## Metadata_Start
## title: CodeScan with Linux/Unix Agents
## original-url : https://knowledgebase.autorabit.com/docs/codescan-with-linuxunix-agents
## article-id : b76e0b87-3770-46ae-b13c-65c8e6e37bcb
## seo-title : 
## description : 
## Metadata_End
To fail a Jenkins job based on the outcome of your Quality gate takes a bit of setting up but is a great way to track the health of your projects from Jenkins. This is achieved with our SFDX plugin.

## Requirements
You will need:

* Jenkins

## Setup Jenkins

1. In Jenkins, create a **[credential](https://docs.cloudbees.com/docs/cloudbees-ci/latest/cloud-secure-guide/injecting-secrets){target="_blank"}** containing your CodeScan security token ([learn how to find security token here](https://knowledgebase.autorabit.com/codescan/docs/generating-a-security-token){target="_blank"}).
2. Create a **new Pipeline**.
3. In the **Pipeline script** section you will need to paste in the code with the highlighted variables changed, these are:
    * Your ***credential_name*** should be the name of the credential you created.
    * ***my_project*** should be the project key you would like to assign to your project.
    * ***my_organization*** should be your Organization Key ([learn how to find this here](https://knowledgebase.autorabit.com/codescan/docs/finding-your-organization-key){target="_blank"}).
   
```
node {

    stage('Pull from Git') {

      git 'https://wherever.com/me/my-repo.git'

    }

    withCredentials([string(credentialsId: 'credential_name', variable: 'codescan_token')]) {
    stage('CodeScan') {
      sh '''
        export PATH="$(pwd)/.sfdx-install/bin/:$PATH"
        if [ ! -f .sfdx-install/bin/sfdx ]; then
          mkdir .sfdx-install
          wget -q https://developer.salesforce.com/media/salesforce-cli/sfdx-linux-amd64.tar.xz -O .sfdx-install/sfdx.tar.xz
          tar xJf .sfdx-install/sfdx.tar.xz -C .sfdx-install --strip-components 1
          echo y|sfdx plugins:install sfdx-codescan-plugin
sfdx plugins:update
        fi
        sfdx codescan:run --token=$codescan_token --projectkey=my_project --organization=my_organization
        exit $?
      '''       }
   } }
```
4. Run the **pipeline**. If everything is set up correctly and your Quality Gate passes, you will be able to see you pipeline pass.
5. If your Quality Gate fails, you will see the error in the CodeScan stage of the build.
