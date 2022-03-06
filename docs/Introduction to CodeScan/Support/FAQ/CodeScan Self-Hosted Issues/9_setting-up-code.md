## Metadata_Start
## title: Setting up CodeScan for use with a Proxy
## original-url : https://knowledgebase.autorabit.com/docs/setting-up-codescan-for-use-with-a-proxy
## article-id : 6dc9eb48-09b9-4488-9b50-c9f7d21fc05a
## seo-title : 
## description : 
## Metadata_End
To configure CodeScan for use in a network with a proxy you will need to set the following settings in your **antbuild.properties** file (version **3.6-RC3+**) or as parameters of your Jenkins job.

**http.proxyHost, http.proxyPort** and optionally **http.proxyUser** and **http.proxyPassword**

Older versions require you to set the above parameters and the following parameters in -**DANT_OPTS**:

**https.proxyHost**, **https.proxyPort** and optionally **https.proxyUser** and **https.proxyPassword**

Also, if your SonarQube™ server is not localhost and your proxy doesn’t resolve internally, you’ll need to add the SonarQube™ server host to **http.nonProxyHosts** to ensure that contacting the SonarQube™ server doesn’t go through the proxy. The value in **http.nonProxyHosts** MUST match the **sonar.host.url** value in the **antbuild.xml** file (minus the port number) or it will not connect.

For example, **antbuild.xml**
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28360%29.png){height="" width=""}

and **antbuild.properties**
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28361%29.png){height="" width=""}
