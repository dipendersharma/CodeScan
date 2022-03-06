## Metadata_Start
## title: Installing CodeScan for IntelliJ
## original-url : https://knowledgebase.autorabit.com/docs/installing-codescan-for-intellij
## article-id : 27d1331a-9e16-4b8b-b2ff-60b6ab74d098
## seo-title : 
## description : 
## Metadata_End
The **CodeScan IntelliJ** plugin provides on-the-fly feedback to developers on bugs and quality issues, it is a fully-integrated user experience in the IntelliJ IDE.

The plugin is derived from **[SonarLint™](https://www.sonarlint.org/){target="_blank"}**.
:::(Info) (Note:)
You must aware that currently the CodeScan and VS Code Plugin will not work along with the SonarLint™ installation, so first you must uninstall SonarLint™.
:::
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28298%29.png){height="" width=""}


## Installation
You will need:

* For **Self Hosted**: a working **SonarQube™ (7.9+)** installation and  licensed **CodeScan (4.4+) plugin** to get started (see [here](https://knowledgebase.autorabit.com/codescan/docs/installation-methods){target="_blank"}).
* For **Cloud**: A CodeScan Cloud organization with a valid license or trial.
* NodeJS for Javascript support.

To install CodeScan for IntelliJ:

* Navigate to the **Settings > Plugins**.
* Click on **Marketplace** tab at the top of the settings window,
* Search CodeScan and install the plugin.
* Restart **IntelliJ** for the changes to take effect.

## Setup Connected Mode
Set up Configuration with CodeScan following the steps below if you need to set up a new one.

1. Go to **Settings** (preferences on Mac).
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28299%29.png){height="" width=""}

2. Select or double click on **Tools** and choose **CodeScan** in the dropdown.
3. You will see another **Settings** tab under which you can see the (**+**) icon, click on it.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28300%29.png){height="" width=""}

:::(Info) (Note:)
Make sure you select the checkbox which says **Automatically trigger analysis**.
:::
4. It opens a new popup window, where you have to give the **Configuration name** and choose the **connection type** of your preference.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28301%29.png){height="" width=""}
5. Click **next**.
6. Now it will take you to another window where you can enter your **token**.
:::(Info) (Note:)
If you are a CodeScan Cloud user, clicking on create token takes you directly to CodeScan Cloud window where you can generate the token.
:::
7. Click **Next** after you enter the token.
8. A new window shows up where you can choose the **Organization** (If you are part of multiple organizations) which you want to configure.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28302%29.png){height="" width=""}
9. Once you choose the **Organization**, click on **Next** and then **Finish**.

To Bind the project with CodeScan:

1. Go to **File > Settings > CodeScan > Project settings**.
2. Select the checkbox which says **Bind the project with CodeScan/CodeScan Cloud**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28303%29.png){height="" width=""}

3. Select the **Connection** under the **Project binding** that you have just setup or choose from the existing one and the project you want to bind and analyze. 
4. Click on **Apply**, for the changes to be applied.
5. Now You will be able to see the errors under the CodeScan window at the bottom in the IDE if there are any, automatically, for the file which is open.
6. If the errors don't show up immediately, reopen the **file** and you will be able to see the changes.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28304%29.png){height="" width=""}
