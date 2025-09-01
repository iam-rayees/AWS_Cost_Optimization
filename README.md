# AWS_Cost_Optimization
This python script will be implemented using AWS Lambda function, Boto3 module to list out the stale EBS snapshots on AWS account and delete them

1)Public cloud has solved the problem of :
a)Maintenance overhead of server - Purchasing the servers, Hiring a separate team for server maintenance etc
b)Infrastructure cost reduction - Setting up a data center incurs huge costs

So for Startups and mid-scale companies, The best solution is public cloud.

2)Even After moving to the Cloud, "Using resources on the cloud efficiently" is very important to control the cloud bills. 
Example:
a)A team member has created a EC2 instance and attached a 80GB volume to this instance. As he/she was working on sensitive information, they were taking back ups(snapshots) on daily basis. After developing the feature completely, Developer has terminated the instance but forget to delete volume, snapshots. These volume and snapshots remains stale and AWS was billing for it. 

b)A team member has created a S3 bucket and uploaded some important files with limited access. Once the new feature of application has launched, Teammate forget to empty and delete the bucket. This again incurs AWS cloud billing to the organization.

c)A team member spinned up a EKS cluster and forget to tear it down after delivering application to customer. This also incurs charges form AWS.

Likewise there are 200 AWS services, If having stale resources running as described above, It will cost huge amount to organization. 

Hence Cloud Cost Optimization Came into picture. Its one of the primary responsibility of the devops engineers to optimize the cloud cost by identifying the stale resources on the cloud and remove them instantly. 

A)Practical:
1)Write AWS lambda function, using python code along with boto3 Module which will communicate with AWS APIs. 
2)We will not write lambda function for all AWS services at a time. Instead lambda functions are written individually. 
3)In this practical, Lambda function is written to list out stale Snapshots on the AWS cloud. It will also check if snapshot is still in use by a volume attached with a instance or this snapshot is stale means volume is deleted or volume is there but instance is deleted. 
4)lambda function is event driven. Hence AWS Cloud watch can be attached to trigger this lambda functions. 

Case1)EC2 instance is deleted but volume and Snapshots remains stale on the AWS account. 
Case2)EC2 instance and volume is deleted but Snapshots remains stale on the AWS account.

Snapshots are not stale if volume(for which snapshots are created) and instance(with which volume is attached) are not deleted and still in use. 

Purpose: To delete the stale snapshots from the AWS account. 
Step1: To list out all the EBS snapshots.
Step2: To Filter out the stale snapshots. 

