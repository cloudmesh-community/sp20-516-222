# Volume Management on Clouds

* sp20-516-222 Peter McCandless

## Introduction

Volume on a physical disk is defined by Microsoft as “a unit of disk space composed as one or more sections of one or more disks” with a simple volume being a single portion of one disk [@www-sp20-516-222-MicrosoftTermonology].

![Volume on a physical disk in Windows](images/Windows-volume-example.png){#fig:sp20-516-222-physicaldisk width=lin}

![Volume on a physical disk in Apple File System](images/AFS-volume-example.jpg){#fig:sp20-516-222-physicaldiskAPF width=lin}

Volume in the cloud can be manipulated to optimally accommodate the process being performed and the data being stored in the cloud.  There are a few types of storage in the cloud.  File storage typically takes the same hierarchical structure as a directory with a path to each file.  Object storage usually takes the form of a data lake in which unstructured data is labeled with metadata that is used to locate the data for processing and analysis.  Block storage volumes with specified sizes are created as needed and can be mounted to virtual machines [@www-sp20-516-222-CloudStorage].  While the space used to host a cloud file or object storage system may technically be a volume, cloud providers typically reserve the the term 'volume' for describing block storage. 



   
[3] <https://docs.cloud.oracle.com/en-us/iaas/Content/Block/Concepts/overview.htm>
