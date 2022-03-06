## Metadata_Start
## title: java.lang.OutOfMemoryError: GC overhead limit exceeded
## original-url : https://knowledgebase.autorabit.com/docs/javalangoutofmemoryerror-gc-overhead-limit-exceeded
## article-id : b113f673-fd7c-4ab6-93b3-13a139b2ecdb
## seo-title : Java Launguage Out of Memory Error - CodeScan
## description : java.lang.OutOfMemoryError can be solved by manually adding a parameter to your Ant environment path variable. Visit here to learn the process for this
## Metadata_End
This error can be solved by manually adding a parameter to your Ant environment path variable.

**In Windows:**
```
set ANT_OPTS=%ANT_OPTS% -Xmx2048M
```

**In Linux/OS X:**
```
export ANT_OPTS=$ANT_OPTS -Xmx2048M
```

If the problem persists, please contact [support@codescan.io](http://support@codescan.io){target="_blank"}
