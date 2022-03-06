## Metadata_Start
## title: License Errors
## original-url : https://knowledgebase.autorabit.com/docs/license-errors
## article-id : 698d2afe-1f97-4f6d-826d-085ea5006543
## seo-title : 
## description : 
## Metadata_End
## Proxy Errors

The most common problem with licensing problems are when your network has a proxy. This can cause licensing problems including:

* **101**: Couldn’t fetch license for unlicensed project
* **104**: Couldn’t fetch license: No response given

**Couldn't fetch license for unlicensed product** is sometimes coupled with something similar to:

* **JsonSyntaxException**: com.google.gson.stream.MalformedJsonException: Expected EOF near <!DOCTYPE html PUBLIC "-//W3C//DTD

This is the proxy replying with an HTML error page when a JSON object is expected.

See **here** for instructions on how to set up CodeScan on a network with a proxy.

## Version Errors

Licensing version problems can occur with older versions of CodeScan. When this occurs, you will see the following error:

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

License is not valid:

License is not for this product

Code: 7

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

This can be avoided by updating to the latest version of CodeScan.

If this is not an option, contact [Support](https://www.codescan.io/contact/){target="_blank"} for assistance and we will provide you with the appropriate license version.

## Line Count Problems

Licensing problems can occur when you are operating outside the Terms of Service.

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

License is not valid:

Lines exceed your license (6878 > 1000)

Code: 103

More information: [http://www.code-scan.com/troubleshooting/license/](http://www.code-scan.com/troubleshooting/license/){target="_blank"}

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

This can be avoided by increasing your license limit or reducing the lines of code you are scanning.

Please contact [Support](https://www.codescan.io/contact/){target="_blank"} for any queries about your license.
