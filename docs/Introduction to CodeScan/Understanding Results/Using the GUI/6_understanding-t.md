## Metadata_Start
## title: Understanding the New Code Tab
## original-url : https://knowledgebase.autorabit.com/docs/understanding-the-new-code-tab
## article-id : a759ad30-44c3-4c7f-a916-a43f710d4e24
## seo-title : 
## description : 
## Metadata_End
SonarQube™’s **New Code** tab is a great way to keep track of new issues in your project.

How the **New Code** is set determines what issues are displayed as new issues. There are several options for this. The **New Code** can be configured for the specific project, navigate to the **Project Settings > New Code** menu from the project dashboard.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-9187UG7Y.png){height="" width=""}

The **New Code** settings can be configured for the project or each branch by clicking on the settings wheel (![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-P2L8U745.png)) at the bottom of this page.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-NOSP68D8.png){height="" width=""}


### Date
By entering a date in the format **yyyy-mm-dd**, SonarQube™ will show the issues that have arisen since that date.

### Number of days
By entering a single number, SonarQube™ will show the issues that have arisen since that number of days ago. Keep in mind that the issues found in the last **5 days** will not be the same a week from now.

### Previous version
By using the ***previous_version*** setting, the New Code will be tracked from the previous version set with the ***sonar.projectVersion*** parameter or from the Activity page.

**For example**, a scan is run on a project with the ***sonar.projectVersion*** ***1.0*** . After time, the project’s ***sonar.projectVersion*** is set to ***1.1***. The New Code Period set to ***previous_version*** would display all issues that have arisen since ***sonar.projectVersion*** ***1.0***.

### Reference Branch
By using the reference branch option, the tool will compare all issues in the current branch to those in the specified reference branch. The New Code Tab will display the delta of those issues.

**For example**, the main branch of your project is pointing to a production environment. A second branch in your project is pointing at a developer environment.  By defining the main branch as the reference for the second branch, you will be able to track new issues created in that developer environment.

### Specific version
By entering your projects required ***sonar.projectVersion***, the New Code Period will display all issues that have arisen since that specific version.

**For example**, a scan is run on a project with the ***sonar.projectVersion*** ***BASELINE***. The project’s ***sonar.projectVersion*** is then set to ***DEVELOPMENT*** and all necessary scans are run over time. The New Code Period set to ***BASELINE*** would display all issues that have arisen since the original scan.

It is important to note that all violations, when they were introduced and the version they are introduced in are tracked. The New Code Period only filters this information on the project’s Overview dashboard and the Issues screen.

## Abnormalities
### Added Files
If you are baselining your projects with a full code base and using the same project key to compare branches of your code, some problems can arise. If the branch does not contain your full code base and you add files to your branch that were present in the initial baseline scan, it will count the files added as new files. This means all the violations present in those files will register as new violations.

There are two options to avoid this:

1. Make sure your entire codebase is present in the branch, not just the files you are working on.
2. Baseline your project with the full code base before every scan.

### Only One Version
If there is only one version present in your project and the New Code Period is set to its default (***previous_version***), the New Code Period may not display properly. To display the New Code Period correctly, set the versions of your project scans with ***sonar.projectVersion*** or set the New Code Period to a certain date or number of days as mentioned above.

### More information:
To explore more on SonarQube™ click here, [SonarQube™: Clean As You Code](https://docs.sonarqube.org/latest/user-guide/clean-as-you-code/){target="_blank"}
