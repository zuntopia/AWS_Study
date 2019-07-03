AZ=`curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone`
export AWS_DEFAULT_REGION=${AZ::-1}

# Obtain latest Linux AMI
AMI=$(aws ssm get-parameters --names /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2 --query 'Parameters[0].[Value]' --output text)
echo $AMI

sudo snap install aws-cli --classic

AZ=`curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone`
export AWS_DEFAULT_REGION=${AZ::-1}

# Obtain latest Linux AMI

AMI=$(aws ssm get-parameters --names /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2 --query 'Parameters[0].[Value]' --output text)
echo $AMI

# Subnet
SUBNET=$(aws ec2 describe-subnets --filters 'Name=tag:Name,Values=Public Subnet' --query Subnets[].SubnetId --output text)
echo $SUBNET

# Security Group
SG=$(aws ec2 describe-security-groups --filters Name=group-name,Values=WebSecurityGroup --query SecurityGroups[].GroupId --output text)
echo $SG

#User Data
wget https://us-west-2-tcprod.s3.amazonaws.com/courses/ILT-TF-100-SYSOPS/v3.3.7/lab-2-ec2-linux/scripts/UserData.txt
cat UserData.txt 

# Launch Instance
INSTANCE=$(\
   aws ec2 run-instances \
   --image-id $AMI \
   --subnet-id $SUBNET \
   --security-group-ids $SG \
   --user-data file:///home/ubuntu/UserData.txt \
   --instance-type t2.micro \
   --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=Web Server}]' \
   --query 'Instances[*].InstanceId' \
   --output text \
   )
