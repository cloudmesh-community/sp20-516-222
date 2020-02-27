# Volume Management on Oracle sp20-516-222, McCandless, Peter

:o2: Add References

:o2: Add Images

Please answer the tests and dont delete them.

:o2: test: what comes after a headline?   
A blank line

:o2: test: how are indents managed in markdown in lists?
1. Add first nubered item
2. Add second numbered item
    1. Add sublist by using four spaces and number or unordered sublist with * - or +
    2. Add additoional items in sublist
        + use another four spaces to add sub-sublist (this one unodered using +)
    3. Continue sublist
3. Continue list  
Add two trailing spaces to the end of a line for a line break (such as after the word "list" in the preceding line).

:o2: test: why are we not useing you’ll  
Technical and scientific writing avoids use of pronouns.

## Oracle Cloud Infrastructure Object Storage

Data stored as objects in Oracle Cloud can be up to 50 GB in size. Once data is uploaded to Object Storage it can be accessed from anywhere, as opposed to network-attached storage for which access is limited by geographical area.  Object Storage is useful to store large amounts of data that changes infrequently. Some typical use cases for Object Storage include large volumes of unstructured data, archiving and backup, and file sharing.

## Oracle Cloud Infrastructure Block Volume Service

A block volume is a virtual disk that provides persistent block storage space for Oracle Cloud Infrastructure instances.  After creating an instance in the oracle cloud, it is possible to connect a block storage volume to the instance.  Oracle Cloud block volumes can range from 1GB to 2TB, and a maximum of 10 block volumes can be attached to the same instance.  The volume can then be used similarly to a physical hard drive in that the volume can be removed from the instance and attached or connected to another instance.  The volume can also be tailored to meet the needs of the application or storage.  
 
## Example of connecting a block volume to an instance

To connect the volume, you need the following information:
* iSCSI IP Address
* iSCSI Port numbers
* CHAP  credentials (if you enabled CHAP)
* IQN 

