# AWS Commands for EC2 instance
 
Basics and Advanced commands which is usefull for setting up and running Amazon AMI EC2 instance
 
## Mounting an extra storage eg HDD cold storage 
Adding a storage to the running instance. (You should have already done the volume attach to the instance from the AWS Management Console)
` sudo mount /dev/[storage_name] /media/NewVol/` <br>
[storage_name] 
:This should be found out by your own. This can be found out by checking the directory list using ```ls``` command in /dev/ folder before and after you attach the volume (Notice the change in it) to the instance via AWS Management Console.
<br>some common names look like nvme1n1 or sdf or xdf


## Copying files from/to s3 
` aws s3 cp filename_from filename_to `

## Copying folder from local storage to aws s3 
As the usage of cp do not help in copying folder from teh instance to the s3 cloud we utilise sync <br>
` aws s3 sync folder_to_copy S3_URL `
