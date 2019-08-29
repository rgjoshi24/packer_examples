# packer_examples
Has example packer files to create images

To install packer on Linux

In a new tab, navigate to https://packer.io/downloads.html

Right-click the 64-bit link in the Linux section and choose Copy link address

On your Linux instance

Become the root user:

  sudo su
  
Change directory to /usr/local/bin:

  cd /usr/local/bin
  
Download the Packer installer:

  wget <Packer_Link>
  
Extract the file:

  unzip packer_1.2.4_linux_amd64.zip
  
Remove the Packer ZIP file:

  rm packer_1.2.4_linux_amd64.zip
  
Exit the root user session:

  exit
  
Verify that Packer works

  packer --version
  
To verify the json file 

 packer validate packer_<names>.json
  
Build an AMI using packer.json

We need to view a more current AMI for our base_AMI variable. To find this information:
  Switch back to the AWS Console tab in your browser
  Navigate to the EC2 service
  Click Launch Instance
  Copy the AMI ID at the end of the "Amazon Linux AMI" line

For our vpc_id:
  Navigate to the VPC service
  Click Your VPCs
  Copy the VPC ID

For our subnet_id:
  Click Subnets
  Check the box to the left of the name on the first subnet in the list
  Ensure that Auto-assign Public IP is "yes" for this subnet
  Copy the Subnet ID

We will use these values to populate our next command:
  
packer build -var 'ami_name=ami-[USERNAME]' -var 'base_ami=[AMI_ID]' -var 'vpc_id=[VPC_ID]' -var 'subnet_id=[SUBNET_ID]' packer.json

Once the command has completed, copy the AMI ID from the output

In the AWS Console tab in your browser, navigate to the EC2 service again

Click AMIs to verify your new AMI is listed
