 # SETTING UP A SCALABLE FILE STORAGE SYSTEM USING AMAZON ELASTIC FILE SYSTEM
  ## AIM
       To  setting up a scalable file storage system using Amazon Elastic File System (EFS) for two EC2 instances in different availability zones. 
## PROBLEM STATEMENT
    Explain about the Experiment.

## ALGORITHM
 ### Step 1: Launch Two EC2 Instances in Different Availability Zones

Go to the EC2 service in the AWS Management Console.
Launch two Linux-based EC2 instances (e.g., Amazon Linux 2) and place them in different availability zones within the same VPC.
Assign each instance a security group that allows NFS access on port 2049.
### Step 2: Set Up Security Group for EFS

Create or configure a security group that allows inbound NFS traffic on port 2049 from the security group of both EC2 instances.
Attach this security group to the EFS file system to permit access from both instances.
### Step 3: Create an EFS File System

In the AWS Console, navigate to the EFS service and select Create file system.
Select the same VPC as your EC2 instances and configure mount targets in the availability zones where your instances are located.
Complete the setup and take note of the file system ID (e.g., fs-064645ac116a12816).
### Step 4: Configure EC2 Instances to Access EFS
Instance 1

SSH into the first EC2 instance.
Switch to superuser
Install the HTTP server and EFS utilities
Mount the EFS file system to the web server's root directory
Navigate to the mounted directory and create a sample file:
Instance 2
SSH into the second EC2 instance.
Switch to superuser
Install the HTTP server and EFS utilities
Mount the EFS file system to the web server's root directory
Navigate to the mounted directory, list files, and view the content of the file created on Instance 1
## COMMANDS
EC2 Instance 1

```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
vi file  # Create a file and add some text
```

EC2 Instance 2

```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
ls
cat file  # Verify shared access by reading content created in Instance 1
```

## OUTPUT
### REG NUMBER:212222110050
### NAME:SWETHA N
### Both EC2 instances showing EFS mounting.

 ![386520949-f5b52ed3-eb2d-490e-82a5-62a2cf281aa5](https://github.com/user-attachments/assets/093f64b1-4a2f-4ea7-a0f6-fd3aafe7604e)

 ![386521246-bfd92e79-6b09-45a8-bbf8-e92a96fea7fc](https://github.com/user-attachments/assets/208c927a-c8d3-443f-b2d5-38511e5049fd)

### The creation of a file on Instance 1.

![386521381-63ac874c-c40d-4c56-82e8-743d36f4cca5](https://github.com/user-attachments/assets/9e8e27da-a14d-4463-a391-88c8043a9637)

### The display of that file’s contents on Instance 2 to verify shared access

 ![386521522-1f3e20a3-ace8-49c4-961b-faf48ca08a2f](https://github.com/user-attachments/assets/63696efd-9187-4022-b1c8-2c253bc2fc83)

## RESULT
 
Successfully set up a scalable file storage system using Amazon EFS shared between two Linux EC2 instances in different availability zones, enabling consistent data sharing.
  


