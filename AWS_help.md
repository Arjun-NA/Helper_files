
# AWS Commands for EC2 instance
 
Basics and Advanced commands which is useful for setting up and running Amazon AMI EC2 instance
 
## Mounting an extra storage eg HDD cold storage 
Adding storage to the running instance. (You should have already done the volume attach to the instance from the AWS Management Console)
` sudo mount /dev/[storage_name] /media/NewVol/` <br>
[storage_name] 
: This should be found out on your own. This can be found out by checking the directory list using the ``` ls``` command in /dev/ folder before and after you attach the volume (Notice the change in it) to the instance via AWS Management Console.
<br>some common names look like nvme1n1 or SDF or XDF


## Copying files from/to s3 
` aws s3 cp filename_from filename_to `

## Copying folder from local storage to AWS s3 
As the usage of cp does not help in copying folder from the instance to the s3 cloud we utilize sync <br>
` aws s3 sync folder_to_copy S3_URL `
