## Metadata_Start
## title: Installing CodeScan on a VM (Ubuntu Server)
## original-url : https://knowledgebase.autorabit.com/docs/installing-codescan-on-a-vm-ubuntu-server
## article-id : a777ead1-466a-4664-ae66-0e8923a3f574
## seo-title : 
## description : 
## Metadata_End
This guide assumes that Ubuntu Server has been installed on your VirtualBox virtual machine and you are logged in with sudo privileges and you have an internet connection.

## Install the Salesforce CLI

CodeScan can run scans with the Salesforce CLI and CodeScan plugin.

1. Install both (**Salesforce CLI** and **CodeScan plugin**) by using the following commands:
```
mkdir .sfdx-install
wget -q https://developer.salesforce.com/media/salesforce-cli/sfdx-linux-amd64.tar.xz -O .sfdx-install/sfdx.tar.xz
tar xJf .sfdx-install/sfdx.tar.xz -C .sfdx-install --strip-components 1
sfdx plugins:install sfdx-codescan-plugin
```

## Install JDK 8

CodeScan requires **Java 8** to run.

1. Install **Java 8** using the following command:
```
sudo apt install openjdk-8-jre-headless
```

## Install NodeJS

CodeScan for Lightning requires **NodeJS** to run.

1. Install **NodeJS** using the following command:
  ```
 sudo apt install nodejs
 ```

## Download and Install the SonarQube™

1. To download the **SonarQube™ 8.4.2** archive, use the following command:
```
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.4.2.36762.zip
```
2. If you do not have a program to unzip the archive, to install unzip archive program use the  command.
```
sudo apt install unzip
```
3. Then **unzip** the archive by using command: 
```
unzip sonarqube-8.4.2.36762.zip
```

## Download and Install the CodeScan

1. To download the **CodeScan 4.4.4.1** archive, use the following command:
```
wget http://downloads.code-scan.com/sonar-salesforce-plugin-4.4.4.1.zip
```

2. Then **unzip** the archive by using command:
```
unzip sonar-salesforce-plugin-4.4.4.1.zip
```
 
3. Copy the **.jar file** to the SonarQube plugins folder using command:
```
cp sonar-salesforce-plugin/sonar-salesforce-plugin-4.4.4.1.jar sonarqube-8.4.2.36762/extensions/plugins/
```

## Setup Network
To use CodeScan outside the server, you will need to configure the connection to the host machine.  

1. Shut down the Ubuntu server using the command:
    ```
    shutdown now
    ```
2. In your Virtualbox window, click your virtual machine and then the **Network** section of the details.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28203%29.png){height="" width=""}

3. Click on **Adapter 2** tab, choose **Host-only Adapter** from the **Attached to** field and **VirtualBox Host-Only Ethernet Adapter** from  the **Name** field.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28205%29.png){height="" width=""}

4. Click on **Adapter 1** tab, go to **Advanced > Port Forwarding**.

5. The default port that SonarQube runs on is **Port 9000**. Click on **Add New Rule** button on the right and configure **port 9000** to be accessible.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28207%29.png){height="" width=""}

6. Click **OK** on both windows. Now you’re ready to run a scan and view the results from your host machine.

## Run SonarQube™

1. Start your virtual machine.

3. Log in and start **SonarQube™** using the command:
```
sonarqube-8.4.2.36762/bin/linux-x86-64/sonar.sh start
```

## Apply CodeScan License

1. On your host computer, open your command prompt and use **ipconfig** to find the IP address for the “**Ethernet adapter VirtualBox Host-Only Networ**k”.

2. Copy the **IPv4 address** and open your host computer’s web browser.

3. In the address bar paste the IP address you just copied and add **:9000** for the port you configured as below.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28208%29.png){height="" width=""}

4. If everything is correct, you will see **SonarQube™** loaded in your browser window.

5. Click **Login** at the top right of the screen and use the default credentials (**Login: admin, Password: admin**) to log in as an administrator.

6. Click **Administration** at the top of the screen and then select **CodeScan** on the left of the screen.

7. In the **CodeScan License** field, paste the **license key** you were supplied with and then click **Save**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28209%29.png){height="" width=""}


## Use CodeScan Quality Profiles

1. In SonarQube™, click on **Quality Profiles** at the top of the screen. You will see a list of languages with the rule sets that are configured for them.

2. Scroll down to **Javascript**, find the ruleset **Salesforce Lightning** and click on **Setting cog** (![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28213%29.png)) icon.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28210%29.png){height="" width=""}

3. Select **Set as Default**.

4. Now scroll down and do the same for the **Visualforce & Lightning** language.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28214%29.png){height="" width=""}

## Running a scan

Now you are ready to run a scan.

1. First, create a **security token**. Learn how to create security token go [here](https://knowledgebase.autorabit.com/codescan/docs/generating-a-security-token){target="_blank"}.

3. Using your **security token** and the **IP address** of your server, type the following command into the command prompt:
```
sfdx codescan:run --token <token> --projectkey my-project-key --organization default-organization --server http://<server IP>:9000
```
3. After the analysis has finished, switch back to the browser on your host computer and click on the **Projects** menu at the top of the page.

4. You should now be able to see your project listed.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28215%29.png){height="" width=""}

5. Click on the **project name** that will allow you to explore the measures in more detail.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28216%29.png){height="" width=""}
