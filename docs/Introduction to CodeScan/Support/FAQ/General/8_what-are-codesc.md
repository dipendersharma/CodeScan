## Metadata_Start
## title: What are CodeScan's system requirements?
## original-url : https://knowledgebase.autorabit.com/docs/what-are-codescans-system-requirements
## article-id : 94ac0aa9-4297-4697-96de-3444c0381292
## seo-title : Sonarqube integration or Jenkins integration - CodeScan
## description : Wondering how to set up a Sonarqube integration or Jenkins integration with CodeScan? Visit here to learn more about the system requirements for set up
## Metadata_End
Official requirements for SonarQube™ can be found [here](https://docs.sonarqube.org/latest/){target="_blank"}.
Official requirements for Jenkins can be found [here](https://www.jenkins.io/doc/book/scaling/hardware-recommendations/){target="_blank"}.

An example of a typical CodeScan Self-Hosted requires:

* 2 CPUs (Equivalent to AWS t2.large)
* 8GB RAM
* 100GB Disk
* Modern Linux OS

:::(Info) (Note:)
Depending on your use-case, this may be way too much or too little. As SonarQube™ stores all snapshots for a long time, the data can build up for a large project. Additionally, heavy usage for users would cause more load.
:::
