## Metadata_Start
## title: Enable CodeScan Cloud Metadata Rules (BETA)
## original-url : https://knowledgebase.autorabit.com/docs/enable-codescan-cloud-metadata-rules-beta
## article-id : 4616b863-49b9-492e-983c-afc422205402
## seo-title : 
## description : 
## Metadata_End
This article guides you on how to enable the Salesforce Metadata (BETA) rules on our cloud environment.

1. Login to your CodeScan account.

2. Click on the **Quality profiles** on your main organization page and then click on **create** button. 
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28172%29.png){height="" width=""}
3. Create s new rule by selecting the language as **Salesforce Metadata (BETA)** and give a name to your **new profile**. You can choose parent rule as an optional.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28173%29.png){height="" width=""}

4. Once you have created the new quality profile, you will be taken to a new page where you can click on **Activate More** button on the left side.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28174%29.png){height="" width=""}
5. Now make sure on your left side of the page where you see the name of the rule you created, it is marked as **inactive** which you can activated these rules.

6. Make sure that you activate the four rules mentioned below by clicking on the **Activate** button beside the rule.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28175%29.png){height="" width=""}
    * Record Type ID is Missing
    * Object Permissions should not be permissive
    * Enforce Org Security Settings
    * Custom fields must have a description field

7. Once activated, select the **Active** button under filters (beside the name of the rule).
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28176%29.png){height="" width=""}

8. Now, go to the project you wish to run the analysis with these rules and click on **Project Settings > General settings**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28237%29.png){height="" width=""}

9. Select the **CodeScan** tab and scroll down to **Scope**, where you see **Metadata File Suffixes**. 
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28240%29.png){height="" width=""}

    a. Add the following suffixes for **classic project** and click on **save** button:
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28177%29.png){height="" width=""}
    * settings
    * profile
    * object
    * sharingRules 

    b. Add the following suffixes **sfdx projects**, add then click on **save** button:
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28178%29.png){height="" width=""}

    * settings-meta.xml
    * object-meta.xml
    * profile-meta.xml
    * sharingRules-meta.xml

12. Now, **Run** the **Analysis**. If your metadata files contain issues, you will see that reflected in the issues list. ![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28179%29.png){height="" width=""}

:::(Info) (Note:)
Make sure that the line count will not show up on the line count breakdown as it is not a **language**, however the issues will show up in the issues list as seen in above figure:
:::


 If you're still having trouble setting it up Metadata rules after reading the entire documentation, please contact [support](http://support@codescan.io){target="_blank"} team and we'll be happy to help.
