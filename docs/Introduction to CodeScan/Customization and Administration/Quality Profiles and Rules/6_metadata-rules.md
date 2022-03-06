## Metadata_Start
## title: Metadata Rules
## original-url : https://knowledgebase.autorabit.com/docs/metadata-rules
## article-id : b400e3dd-a6b8-44d5-af9c-b7fd25b69f7a
## seo-title : Metadata Rules on Self Hosted | CodeScan Knowledgebase
## description : As of version 4.4.2, CodeScan has a set of Metadata rules. These allow you to scan your settings to make sure that your Org is secure and clean.
## Metadata_End
As of version **4.4.2**, CodeScan has a set of Metadata rules.

These rules allow you to scan your settings to make sure that your Org is secure and clean.

To enable downloading metadata for your Salesforce project, you will need to change some settings in your project settings. Keep in mind that the following will only work with code being pulled from Salesforce.

1. First, open your Salesforce project and navigate to **Project Settings > General Settings** menu.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28249%29.png){height="" width=""}

2. Next, click the **CodeScan** tab on the left to open the [CodeScan](https://www.codescan.io/){target="_blank"} specific settings and access the **CodeScan Cloud Download Types**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28250%29.png){height="" width=""}

3. The default values will be ApexClass, ApexComponent, ApexPage, ApexTrigger, AuraDefinitionBundle, and LightningComponentBundle. To download all metadata currently checked, you will need to add the following:

    * CustomObject
    * Profile
    * SharingCriteriaRule
    * SharingOwnerRule
    * SharingTerritoryRule
    * Settings

4. After you have added these pakage types, click on **Save** button
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28251%29.png){height="" width=""}
5. To re-run the analysis, go to the **Overview > Project Settings > General Settings** menu. Your metadata files will download and the ruleset will be applied.

### Metadata Rules on Self Hosted
As of CodeScan version **4.4.2**, metadata rules are available in Self Hosted CodeScan.

To pull your metadata, you will need to add the required file types to your **package.xml** file. 

We have provided a package.xml file below download it to get started for Self Hosted CodeScan. Download the XML file from here, 
@(Embed)(https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/package.xml){height="320" width="640"}
