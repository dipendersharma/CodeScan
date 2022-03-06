## Metadata_Start
## title: PKIX Path Building Failed
## original-url : https://knowledgebase.autorabit.com/docs/pkix-path-building-failed
## article-id : a30bc718-5af4-43e6-bb05-1b3b8ed39978
## seo-title : 
## description : 
## Metadata_End
This article should help if you encounter the following error and accompanying stack trace:

```
javax.net.ssl.SSLHandshakeException: 
sun.security.validator.ValidatorException: 
PKIX path building failed: 
sun.security.provider.certpath.SunCertPathBuilderException: 
unable to find valid certification path to requested target.
```

This problem occurs when your Java environment does not trust the certificate of the server running your SonarQube instance. To alleviate this issue, we need to add the server certificate to the Java key store following these steps.

1. You will need **Java keytool**, and the location of your **CACERTS file**. These are typically located in your **JRE** or **JDK** such as this:

```
 ./jdk1.6.0_24/jre/lib/security/cacerts
./jdk-11.0.9/bin/keytool.exe
```

2. Navigate to your server in Chrome, click the **padlock** (![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28359%29.png)) icon on the left of address bar and then click **Certificate**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28354%29.png){height="" width=""}

3. Next, go to **Certification Path > DigiCert Baltimore Root** and then click on **View Certificate**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28355%29.png){height="" width=""}

4. Go to **Details**, click on **Copy to File**.
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28356%29.png){height="" width=""}

5. Select **DER encoding binary X.509 (.CER)** and download it. 
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28357%29.png)
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image%28358%29.png){height="" width=""}

In an **administrative command prompt**, navigate to the directory with your downloaded cert. and add the certification to your **CACERTS** using the keytool (keep in mind the directory syntax will change depending on your OS). 
```
keytool -import -alias MyCert -keystore "C:\Program Files\Java\jdk-11.0.9\lib\security\cacerts" -file cert.cer
```
![image.png](https://cdn.document360.io/8711f4e7-c040-4616-aac9-d947f87e4619/Images/Documentation/image-19LS043D.png){height="" width=""}
