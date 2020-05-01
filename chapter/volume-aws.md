# Volume Management on AWS sp20-516-222, McCandless, Peter

:o2: Add References

:o2: Add Images

AWS offers cloud storage services for each of the three cloud storage types: Amazon Elastic File Service, Amazon Simple Storage Service, and Amazon Elastic Block Store. 

![[@www-sp20-e156-222-awsstorage]](images/awsstorageoptions.PNG){#fig:sp20-516-222-awsstorageoptions width=lin}

## AWS File Storage Services

Amazon Elastic File System (EFS) is a cloud file storage system that, as the name indicates, is elastic and scalable.  EFS uses a hierarchical directory structure common to file storage systems.  Being an elastic system means that the EFS storage volume is able to expand and shrink automatically as files are added and removed.  EFS also includes a Lifecycle Management feature that automatically sorts infrequently used files from a standard storage class into a lower-cost storage class [www-sp20-e516-awsefs].

Also available in AWS are two specialized file systems called FSx.  For Windows applications, Amazon FSx for Windows File Server allows for applications based in Windows to be integrated into the AWS cloud by using a native Windows File System.  Like EFS, Amazon FSx for Windows File Server provides elasticity and scalability automatically.  Amazon FSx for Lustre is designed to be a short-term file storage system for high-performance data processing.  FSx for Lustre is able to display stored objects as files and was created to work with Amazon Simple Storage Service, an object storage service.  Data can be copied from a Simple Storage Service bucket to an FSx for Lustre file system in order to run a compute-intensive workload.  The results can then be written back to the bucket and the file system deleted when the workload has finished [www-sp20-e516-awsFSx].       

## Amazon Simple Storage Service (S3)

Amazon provides an object storage service through its Amazon Storage Service (S3).  Like Amazon EFS, S3 will automatically scale volume to accommodate increased data storage and to meet the demands of running applications [wwww-sp20-e516-awss3].   

## Amazon Elastic Block Store (EBS)

Amazon’s block storage, called Amazon Elastic Block Store (EBS), allows users to choose between four volume types: EBS Provisioned IOPS SSD (io1), EBS General Purpose SSD (gp2), Throughput Optimized HDD (st1), and Cold HDD (sc1).

To be added: image of table for volume types

There are several factors that influence the performance of EBS.  EBS performance for all volumes types is directly related to the storage size allocated to the block.  When using gp2 for example, the block volume size created determines the baseline input/output per second (IOPS) of the application running in the block.  Increasing block size allows more throughput, which can be useful for databases which perform large amounts of sequential input/output.  Since block size also determines the minimum total storage size, more space that is necessary may be used when working with small objects or files.  It is important to understand the volume needs of the data storage and applications before setting up a block storage in order to avoid misusing resources and possibly incurring higher costs.  Finally, optimizing network bandwidth by using optimized Amazon EC2 instances or by using appropriate networking is important for getting the best performance from EBS.  

## Amazon EBS Example: How to Automatically Filter and Delete EBS Volumes with Lambda Functions and CloudWatch

The following example shows how to find unsed EBS volumes, which can then be deleted.  Deleting unused volumes can help control the cost of using the cloud service [@www-sp20-516-222-EBScosteff].

Step 1: Get Started by Opening AWS LambdaAWS Lambda

Step 2: Create a Lambda Function Lambda Function 

Step 3: Click on the Empty Box and Select CloudWatch ScheduleCloudWatch Schedule

![[@@www-sp20-516-222-EBScosteff]](images/Lambdastep3.PNG){#fig:sp20-516-222-Lambdaste3 width=lin}

Step 4: Schedule the Function by Specifying Cron ExpressionCron Expression

![[@@www-sp20-516-222-EBScosteff]](images/Lambdastep4.PNG){#fig:sp20-516-222-Lambdaste3 width=lin}

Step 5: Assign a Role with Necessary PermissionsLambda Permissions

Step 6: Paste the Following Code Snippet After the Trigger is Created.  Code Snippet:

```python
import boto3
ec2 = boto3.resource('ec2',region_name='us-east-1')

def lambda_handler(event, context):
    for vol in ec2.volumes.all():
        if  vol.state=='available':
            if vol.tags is None:
                vid=vol.id
				v=ec2.Volume(vol.id)
                v.delete()
                print "Deleted " +vid
                continue
            for tag in vol.tags:
                if tag['Key'] == 'Name':
                    value=tag['Value']
                    if value != 'DND' and vol.state=='available':
                        vid=vol.id
                        v=ec2.Volume(vol.id)
                        v.delete()
                        print "Deleted " +vid
```

