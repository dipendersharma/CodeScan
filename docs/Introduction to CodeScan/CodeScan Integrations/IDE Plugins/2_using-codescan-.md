## Metadata_Start
## title: Using CodeScan with the Welkin Suite
## original-url : https://knowledgebase.autorabit.com/docs/using-codescan-with-the-welkin-suite
## article-id : 2ddb3868-6b73-4caa-adbb-2bbc253a5f68
## seo-title : Using CodeScan with the Welkin Suite | Welkin Suite Integration
## description : CodeScan within the Welkin Suite provides feedback to developers on bugs and quality issues. Visit to learn how to integrate CodeScan into this environment.
## Metadata_End
Using CodeScan with the Welkin Suite provides on-the-fly feedback to developers on bugs and quality issues, it is a fully-integrated user experience and requires no extra installation of CodeScan.

## Configuration

1. Before you begin configuration you will need:

    * A current CodeScan License.
    * A current licensed installation of the Welkin Suite.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28295%29.png){height="" width=""}

2. Now, add your license to the **Welkin Suite (TWS)** and then follow the below steps:
    * Go to **Tools > Options > External Tools > CodeScan** and enter your **license key**. If you do not have a license key, you can request a trial [here](http://license.code-scan.com/index.php){target="_blank"}.
    * The ***Run CodeScan before build*** option executes CodeScan before each build, but only for files that were changed, and are sent to Salesforce.
    * The ***Raise build errors on certain CodeScan issues*** option cancels the build process in case of errors. It also allows you to specify what priority of violations should be classified as errors.

## Defining a Ruleset
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28296%29.png){height="" width=""}
1. Go to **Tools > CodeScan Apex Ruleset Configuration**.
2. Click **New** and choose **Apex Villagechief template**.
    * This will allow you to modify the [CodeScan ](https://www.codescan.io/){target="_blank"}recommended set of rules rather than starting from scratch.
3. Use the **checkboxes** to select the **rules** you would like to include.
    * Rule parameters and custom priorities are also configurable in this window.
4. Save the **ruleset** when you are completed.
5. Go to **Tools > Options > External Tools > CodeScan** and then select your **ruleset file** as the default ruleset.

## Running a Scan
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28297%29.png){height="" width=""}
1. Right click on the **file** or **project** you would like to scan in the solution explorer and select **Scan with CodeScan**.
2. Now, the **CodeScan Report window** will open and show each violation in a list.

The **Welkin Suite** website also has a great in depth version of this guide, [available here](https://docs.welkinsuite.com/?id=mac:how_does_it_work:integrations:codescan:start&s[]=codescan){target="_blank"}.
