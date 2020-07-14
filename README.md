# aws_code_deploy
## Steps for AWS code deploy using S3 as source
1. Create IAM Roles - CodeDeploy & EC2CodeDeploy
2. Create EC2 instance with the following software packages should install<br/>
     a. Choose AMI: Amazon Linux 2<br/>
     b. Choose AMI role as EC2CodeDeploy<br/>
     c. Choose User Data: for installing required packages.<br/>
     
     
     ```
     #!/bin/bash
     sudo yum -y update
     sudo yum -y install ruby
     sudo yum -y install wget
     cd /home/ec2-user
     wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latest/install
     sudo chmod +x ./install
     sudo ./install auto
     sudo yum install -y python-pip
     sudo pip install awscli`

  d. Security groups: which enable port SSH port 22 and HTTP 80 (for application)<br/>
  e. Launch instance<br/>

3. Goto CodeDeploy Create Application<br/>
4. Create a DeploymentGroup<br/>
