# aws_code_deploy
## Steps for AWS code deploy using S3 as source
 1.  **Create IAM Roles - CodeDeploy & EC2CodeDeploy**
 1.  **Create EC2 instance with the following software packages should install**<br/>
 1.  **Choose AMI: Amazon Linux 2**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/AMI.png)<br/>
 1.  **Choose AMI role as EC2CodeDeploy**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/ConfigureInstance.png)<br/>
 1.  **Choose User Data: for installing required packages.**<br/>
     #!/bin/bash<br/>
     sudo yum -y update<br/>
     sudo yum -y install ruby<br/>
     sudo yum -y install wget<br/>
     cd /home/ec2-user<br/>
     wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latest/install<br/>
     sudo chmod +x ./install<br/>
     sudo ./install auto<br/>
     sudo yum install -y python-pip<br/>
     sudo pip install awscli<br/>

     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/UserData.png)<br/>
 1.  **Security groups: which enable port SSH port 22 and HTTP 80 for application**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/configureSecutiryGroup.png)<br/>     
 1.  **Add tags to your EC2 instance**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/addTags.png)<br/>
 1.  **Launch instance**<br/>
 1.  **Makesure that your bucket should enabled version**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/create_bucket_version.png)<br/>
 1.  **Goto CodeDeploy Create Application**<br/>
 1.  **Create a DeploymentGroup**<br/>
 1.  **Moving Your Application Into GitHub**<br/> for more details [Click Here](https://aws.amazon.com/blogs/devops/automatically-deploy-from-github-using-aws-codedeploy/)
If the application files that you want to deploy are not already in a GitHub repository, you’ll need to set that up. Here’s how you can do it with the getting started sample application. First, download the application files. These examples use Linux / Unix commands.<br/><br/>

 > mkdir codedeploy-sample<br/>
   cd codedeploy-sample<br/>
   curl -O http://s3.amazonaws.com/aws-codedeploy-us-east-1/samples/latest/SampleApp_Linux.zip<br/><br/>

**You can upload SampleApp_Linux.zip file on S3 for further automatic deployment on CodeDeploy Pipeline**
