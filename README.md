# aws_code_deploy
## Steps for AWS code deploy using S3 as source
1. **Create IAM Roles - CodeDeploy & EC2CodeDeploy**
2. **Create EC2 instance with the following software packages should install**<br/>
     a. **Choose AMI: Amazon Linux 2**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/AMI.png)<br/>
     b. **Choose AMI role as EC2CodeDeploy**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/ConfigureInstance.png)<br/>
     c. **Choose User Data: for installing required packages.**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/UserData.png)<br/>
     
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
<br/>
  d. **Security groups: which enable port SSH port 22 and HTTP 80 (for application)**<br/>
  ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/configureSecutiryGroup.png)
  e. **Add tags to your EC2 instance**<br/>
  ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/addTags.png)
  f. **Launch instance**<br/>
3. **Makesure that your bucket should enabled version**<br/>
  ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/create_bucket_version.png)
3. **Goto CodeDeploy Create Application**<br/>
4. **Create a DeploymentGroup**<br/>
