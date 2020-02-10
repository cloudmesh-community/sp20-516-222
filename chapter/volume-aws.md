# Volume Management on AWS sp20-516-222, McCandless, Peter

AWS offers cloud storage services for each of the three cloud storage types: Amazon Elastic File Service, Amazon Simple Storage Service, and Amazon Elastic Block Store. 

## AWS File Storage Services

Amazon Elastic File Service (EFS) for Linux applications is a cloud file storage system that, as the name indicates, is elastic and scalable.  EFS uses a hierarchical directory structure common to file storage systems.  Being an elastic system means that the EFS storage volume is able to expand and shrink automatically as files are added and removed.  EFS also includes a Lifecycle Management feature that automatically sorts infrequently used files from a standard storage class into a lower-cost storage class.

For Windows applications, Amazon FSx for Windows File Server allows for applications based in Windows to be integrated into the AWS cloud by using a native Windows File System.  Like EFS, Amazon FSx for Windows File Server provides elasticity and scalability automatically.

Amazon FSx for Lustre is designed to be a short-term file storage system for high-performance data processing.  FSx for Lustre is able to display stored objects as files and was created to work with Amazon Simple Storage Service, an object storage service.  Data can be copied from a Simple Storage Service bucket to an FSx for Lustre file system in order to run a compute-intensive workload.  The results can then be written back to the bucket and the file system deleted when the workload has finished.       

## Amazon Simple Storage Service (S3)

Amazon provides an object storage service through its Amazon Storage Service (S3).  Like Amazon EFS, S3 will automatically scale volume to accommodate increased data storage and to meet the demands of running applications.   

## Amazon Elastic Block Store (EBS)

Amazon’s block storage, called Amazon Elastic Block Store (EBS), allows users to choose between four volume types: EBS Provisioned IOPS SSD (io1), EBS General Purpose SSD (gp2), Throughput Optimized HDD (st1), and Cold HDD (sc1).

## Amazon EBS Example

