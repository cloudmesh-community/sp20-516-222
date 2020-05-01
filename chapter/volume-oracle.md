# Volume Management on Oracle sp20-516-222, McCandless, Peter

:o2: Add References

:o2: Add Images

Please answer the tests and dont delete them.

:+1: test: what comes after a headline?   
A blank line

:+1: test: how are indents managed in markdown in lists?
1. Add first nubered item
2. Add second numbered item
    1. Add sublist by using four spaces and number or unordered sublist with * - or +
    2. Add additoional item in sublist
        + use another four spaces to add sub-sublist (this one unodered using +)
    3. Continue sublist
3. Continue list  
Add two trailing spaces to the end of a line for a line break (such as after the word "list" in the preceding line).

:+1: test: why are we not useing you’ll  
Technical and scientific writing avoids use of pronouns.

## Oracle Cloud Infrastructure Object Storage

Data stored as objects in Oracle Cloud can be up to 50 GB in size. Once data is uploaded to Object Storage it can be accessed from anywhere, as opposed to network-attached storage for which access is limited by geographical area.  Object Storage is useful to store large amounts of data that changes infrequently. Some typical use cases for Object Storage include large volumes of unstructured data, archiving and backup, and file sharing.

## Oracle Cloud Infrastructure Block Volume Service

A block volume is a virtual disk that provides persistent block storage space for Oracle Cloud Infrastructure instances.  After creating an instance in the oracle cloud, it is possible to connect a block storage volume to the instance.  Oracle Cloud block volumes can range from 1GB to 2TB, and a maximum of 10 block volumes can be attached to the same instance.  The volume can then be used similarly to a physical hard drive in that the volume can be removed from the instance and attached or connected to another instance.  The volume can also be tailored to meet the needs of the application or storage by varying characteristics such as size or file system.  
 
## Example of connecting a block volume to an instance

To connect the volume, you need the following information:
* iSCSI IP Address
* iSCSI Port numbers
* CHAP  credentials (if you enabled CHAP)
* IQN 

1.	Use the Console to obtain the iSCSI data you need to connect the volume:
    a.	Log on to Oracle Cloud Infrastructure.
    b.	Open the navigation menu. Under Core Infrastructure, go to Compute and click Instances.
    c.	Click your instance's name to display the instance details.
    d.	In the Resources section on the Instance Details page, click Attached Block Volumes to view the attached block volume.
    e.	Click the Actions icon (three dots) next to the volume you're interested in, and then click iSCSI Commands and Information.
    The iSCSI Commands and Information dialog box displays your volume’s IP address and port, which you’ll need to know later in this       procedure.
2.	Log in to your instance using a Remote Desktop client.
3.	On your Windows instance, open the iSCSI Initiator. The steps to open the iSCSI Initiator may vary depending on the version of     Windows.
    * For example: Open Server Manager, click Tools, and then select iSCSI Initiator.
4.	In the iSCSI Initiator Properties dialog box, click the Discovery tab, and then click Discover Portal.
5.	Enter the block volume IP Address and Port, and then click OK.
6.	Click the Targets tab.
7.	Under Discovered targets, select the volume IQN.
8.	Click Connect.
9.	Make sure that the Add this connection to the list of favorite targets check box is selected, and then click OK.
10.	You can now format (if needed) and mount the volume. To view a list of mountable iSCSI devices on your instance, in Server Manager,  click File and Storage Services, and then click Disks.  The disk is displayed in the list.

When connecting to a Windows boot volume as a data volume from a second instance, you need to append -IsMultipathEnabled $True to the Connect-IscsiTarget command.

