## Metadata_Start
## title: Installing CodeScan for VS Code
## original-url : https://knowledgebase.autorabit.com/docs/installing-codescan-for-vs-code
## article-id : 07392b38-c829-4e9f-8f82-72996d4c721e
## seo-title : 
## description : 
## Metadata_End

<iframe title="vimeo-player" src="https://player.vimeo.com/video/445022849?h=523918331a" width="640" height="360" frameborder="0" allowfullscreen></iframe>

The **CodeScan VS Code** plugin provides on-the-fly feedback to developers on bugs and quality issues, it is a fully-integrated user experience in VS Code.

## Prerequisites
You will need:

* JDK 11
* NodeJS
* For **Self Hosted**:
    * A working **SonarQube™ (7.9+)** installation
    * A licensed version of **CodeScan (4.3+)** plugin to get started (see here)
* For **CodeScan Cloud**:
    * A CodeScan Cloud account (with valid enterprise or trial license)

* A recent version of **VS Code** installed (**v1.12 or above**)
* If you are working with Salesforce code, you will need the **Salesforce Extensions** for VS Code or at least the **Apex** and **Visualforce plugins**.
* The plugin is derived from **[SonarLint™](https://www.sonarlint.org/){target="_blank"}**.

:::(Info) (Note:)
You must aware that currently the CodeScan and VS Code Plugin will not work along with the SonarLint™ installation, so first you must uninstall SonarLint™.
:::
## Installation

1. In VS Code, go to the Marketplace and download CodeScan.

2. Restart the VS Code.

3. Press **Ctrl + Shift + P** and search Settings to open.

4. Copy and paste the following boilerplate in to get started.
```
"codescan.servers": [
       {
            "serverId": "**************",
            "organizationKey": "**************",
            "serverUrl": "**************",
            "token": "**************"
        },
    ],

    "codescan.project": {
        "serverId": "**************",
        "projectKey": "**************"
    }
```

5. Edit the following in the ***codescan.server**s* section.
6. For **CodeScan Cloud**:
    * Add ***organizationKey*** as your CodeScan Cloud organization key ([Where do I find this?](https://knowledgebase.autorabit.com/codescan/docs/finding-your-organization-key){target="_blank"})
      * If you are using CodeScan Self Hosted, please enter ***default-organization***.
    * Add ***token*** with a token generated in [here](https://app.codescan.io/){target="_blank"} in CodeScan Cloud.
    * Add server ***Url*** as ***https://app.codescan.io/***
    * Add server ***Id*** with a value you will remember.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-4DXYDPNX.png){height="" width=""}

7. For **Self-Hosted CodeScan**:

* Add ***token*** with a token generated in SonarQube™.

* Add server ***Url*** as your SonarQube™ server URL (Default is **http://localhost:9000**).

* Add server ***Id*** with a value you will remember.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-9EJNS5NU.png){height="" width=""}

8. Edit the following in ***codescan.project***
* Add ***projectKey*** with the key of the project you would like to use the settings from ([Where do I find this?](https://knowledgebase.autorabit.com/codescan/docs/how-to-find-a-project-key-in-codescan){target="_blank"}).

* Add ***serverId*** with the ***serverId*** you used when editing your ***codescan.servers*** settings.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-WDWUVYZT.png){height="" width=""}

9. Now hit **Ctrl+Shift+P (Windows/Linux)** or **Shift+Command+P(Mac)** to open the Command Palette.

10. Type in CodeScan to bring up the CodeScan commands and run “**Update CodeScan binding to SonarQube/CodeScan Cloud**”. If any changes are made on the SonarQube™ server you should repeat this step.
11. Open a file, you should see the issues in your code underlined.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-NA9LYN17.png){height="" width=""}

## VS Code behind a proxy
VS Code extensions can be difficult to use behind a proxy.  

To point CodeScan at the correct proxy, all it takes is a single environment variable for your system.
The environment variable is:
```
JAVA_TOOL_OPTIONS
```
The value should be: 
-Dhttp.proxyHost=[YOUR_PROXY_HOST] -Dhttp.proxyPort=[YOUR_PROXY_PORT]

-Dhttps.proxyHost=[YOUR_PROXY_HOST] -Dhttps.proxyPort=[YOUR_PROXY_PORT]

-Dhttp.nonProxyHosts="localhost|127.0.0.1"

If the proxy has a username and password you can provide those in the ***-Dhttps.proxyUser=your_username*** and ***-Dhttps.proxyPassword=your_password*** parameters.

## Self Signed Certificates
If you are connecting to a server with self signed certificates you will need to specify them for your **Java** and **Node** installations. 

For your Java installation, you can find the documentation [here](https://docs.oracle.com/en/java/javase/11/security/java-security-overview1.html#GUID-054AD71D-D449-47FF-B6F7-F416DA821D46){target="_blank"}.

For your Node installation, please add the environment variable ***NODEEXTRACA_CERTS*** with the path to your certificate file as a value.  eg:  ***/usr/local/share/ca-certificates/YOUR_CERT.crt***

## Troubleshooting
Some useful debugging information is available under the Output window under the ‘**CodeScan**’ tab.

CodeScan should automatically find the JRE installed on your computer. If you are having trouble you can specify the path using ***sonarlint.ls.javaHome*** variable in your VS Code Settings.

You can check for any serious errors by going to **Help > Toggle Developer Tools** to bring up the console.

You can also contact us at the [CodeScan Support Page](https://support.autorabit.com/portal/en/home){target="_blank"}. Feel free to ask questions, report issues, and give suggestions.
