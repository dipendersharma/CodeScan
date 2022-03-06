## Metadata_Start
## title: Scan CodeScan Cloud projects in Azure DevOps
## original-url : https://knowledgebase.autorabit.com/docs/scan-codescan-cloud-projects-in-azure-devops
## article-id : 0a842447-aa72-40e8-9024-2d0758701724
## seo-title : CodeScan and Azure DevOps Integration 
## description : CodeScan offers an Azure DevOps integration to cover your development environment. Visit here to learn how to scan CodeScan cloud projects with Azure DevOps.
## Metadata_End
## Prerequisites

* CodeScan version **4.4+**
* An Azure DevOps Project for your Salesforce code

## Install the CodeScan Cloud Extension

1. At the top right of your screen, click on the **Marketplace** and then select **Browse Marketplace**.
2. Search for **CodeScan**, select the **CodeScan Cloud extension** and then click **Get it free**.
3. Select your **account** and complete the installation.

## Setup

* On your Project Dashboard, select **Pipeline>Pipelines** and create a **new Pipeline**.
* Once you are in the "**Where is your code?**" page, click **Use the classic editor to create a pipeline without YAML**.  

Follow the instructions below for your source code location.

### Azure DevOps Repo

1. Select **Azure Repos Git** and your **Repository name**.

2. For your default branch, select the **branch** you would like to check pull requests against. Keep this branch name in mind, we will use it later in the setup. Click **Continue**.
3. On the Select a Template page, select the **Salesforce with CodeScan Cloud** template and click **Apply**.
4. In the Agent pool dropdown menu, select **Azure Pipelines**.
5. In the Agent Specification dropdown menu, select **ubuntu-20.04**.
6. Click the **Prepare Analysis on CodeScan Cloud** section, create a new Service Endpoint.
    * You will need a token from your CodeScan Cloud account for this step. Learn how to create security token [here](https://knowledgebase.autorabit.com/codescan/docs/generating-a-security-token){target="_blank"}.
    * Add a name for your connection.
    * Make sure to verify the connection before leaving the pop-up.

7. Select your new Service Endpoint and the Organisation you would like to connect to from the dropdown menu.
    * If you are not sure, the Organisation key is available at the top left of your Organisation page.
8. Select **Use standalone scanner** under the **Choose a way to run the analysis**.
9. Under **Mode**, select the **make sure Manually provide configuration** checkbox.

### Now, in CodeScan Cloud we can set up the project.

1. In your selected [CodeScan Cloud](https://www.codescan.io/products/cloud/){target="_blank"} organisation, navigate to **Administration > Projects Management**.
2. Click **Create Project**.
3. Enter your desired **Project Name** and **Project Key** and click **Create**. Keep these in mind, we'll need them in a second.
4. Click on your new empty project and navigate to **Administration > Branches and Pull Requests**.
5. Change your main branch name to the name of the default branch that you selected.

### Now, back to Azure DevOps.

1. Enter the **Project Name** and **Project Key** you just created.
2. Click **Save and Queue** and let the analysis complete to see your results in CodeScan Cloud.

## Triggering Builds from an Azure Devops Repository

To trigger the builds you will need to create a build policy on the branch you would like to check pull requests against.

1. Navigate to **Repos > Branches**.
2. Click on the **More** menu for the desired branch and click **Branch Policies**.
3. In the Build Validation section, add a new build policy.
4. Select your **new pipeline**, select Automatic for the Trigger settings and choose your policy requirements.

This pipeline will now run when:

* Pull requests are created against the branch
* Pull requests are updated
* Pull requests are merged

And the project branches on CodeScan Cloud will be updated accordingly.

## Breaking the builds

To break the builds based on the Quality Gate once this analysis has run, you can add a powershell script to the pipeline.

1. First create a **[security token](https://knowledgebase.autorabit.com/codescan/docs/generating-a-security-token){target="_blank"}** and add it as a variable named **CODESCAN_TOKEN** in your pipeline Variables menu. 
2. In your pipeline Agent Specification, change the dropdown to **windows-2019**.
3. Add a PowerShell step to your pipeline after the Publish Quality Gate step and add the following script inline, changing the bold **project_key** to your actual project key.
```
$token = [System.Text.Encoding]::UTF8.GetBytes($env:CODESCAN_TOKEN + ":")
$base64 = [System.Convert]::ToBase64String($token)
 
$basicAuth = [string]::Format("Basic {0}", $base64)
$headers = @{ Authorization = $basicAuth }

$URL = [string]::Format("https://app.codescan.io/api/qualitygates/project_status?projectKey=azure-devops&branch {0}", $env:BUILD_SOURCEBRANCHNAME)

$result = Invoke-RestMethod -Method Get -Uri $URL  -Headers $headers
$result | ConvertTo-Json | Write-Host
 
if ($result.projectStatus.status -eq "OK") {
Write-Host "Quality Gate Succeeded"
}else{
throw "Quality Gate failed"
}
```

The pipeline will now fail if the quality gates for the project are not passed.
