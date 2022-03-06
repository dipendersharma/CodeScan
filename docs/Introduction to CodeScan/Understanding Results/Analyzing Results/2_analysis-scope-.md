## Metadata_Start
## title: Analysis Scope on Codescan Cloud
## original-url : https://knowledgebase.autorabit.com/docs/analysis-scope-on-codescan-cloud
## article-id : 8e923959-be27-47de-a229-8f4a22a85013
## seo-title : 
## description : 
## Metadata_End
Analysis scope is something which helps you to narrow down the results to only the relevant issues. This in turn reduces the noise and the issues from the rules which may not be relevant for certain files. Its key features include:

* Helps in excluding certain files from detecting specific issues.
* It helps you to completely ignore some files.
* Exclude files from duplications detection and coverage calculations.

Follow the steps below to use the **Analysis Scope** feature on CodeScan cloud.

1. Open the project under the organization on which you need to run the analysis and navigate to **Project Settings > General Settings > Analysis Scope**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28285%29.png){height="" width=""}

2. Now you will be able to view the tab, under which you can select your required specification to enable this feature during the analysis

 * **Wildcards:** If you scroll the tab further to the end, you can see a portion which says wildcards under which there are rules and examples which help you understand how to enter the specifications or part of the file name to enable this feature. To know more about Wildcards, click on [Learn More](https://app.codescan.io/documentation/project-administration/narrowing-the-focus/){target="_blank"}.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-C0HJYQMZ.png)
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-W476DWV1.png){height="" width=""}

3. If we go under **files**, we will be able to view two options as follows:
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28287%29.png){height="" width=""}


    * **Source File Exclusions**: to exclude source code files
Specifying an exclusion means that everything under your directory will be included in analysis except the files with paths that match your exclusion pattern.

    * **Source File Inclusions**: It helps you to include only the specific source code files in the analysis
In a few corner cases, it is necessary to be explicit about what's included in analysis and leave out everything else, but that is not the normal case, and setting inclusions should not be the first thing you try when configuring a new project.

4. Once the analysis is completed, go to the **code** tab to view the files as per your specified settings.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28288%29.png){height="" width=""}

Here are a couple of implementation examples:

* **For Source File Exclusion**:
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28289%29.png)
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28290%29.png){height="" width=""}

* **For Source File Inclusion**:
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28291%29.png)
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28292%29.png){height="" width=""}
