# AWS_CodeDeploy_Example
<br />
Please make sure that you add the following files to your project for this to work
<br />
&nbsp;&nbsp;&nbsp;&nbsp; appspec.yml
<br />
&nbsp;&nbsp;&nbsp;&nbsp; the entire scripts folder
<br />
<a href="https://www.youtube.com/watch?v=F6oLG-LyIhc&t=372s">Tutorial</a>
<br />
<br />
1. Create IAM Roles
<br />
CodeDeploy & EC2CodeDeploy
<br />
2. Create EC2 instance with following categories
<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;    a. Choose AMI: Amazon Linux AMI
    <br />
    <br />
&nbsp;&nbsp;&nbsp;&nbsp;    b. Choose Instance type: t2.micro
    <br />
    <br />
 &nbsp;&nbsp;&nbsp;&nbsp;   c. Configure Instance: Choose EC2CodeDeploy IAM role
    <br />
    <br />
  &nbsp;&nbsp;&nbsp;&nbsp;  d. Tag Instance: Name it what you please
    <br />
    <br />
  &nbsp;&nbsp;&nbsp;&nbsp;  e. Configure Security Group: 
    <br />
    <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;        HTTP TCP 80 0.0.0.0/0
        <br />
        <br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;      HTTP TCP 80 ::/0
        <br />
        <br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;      SSH TCP 22 (YOUR IP ADDRESS)
        <br />
        <br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;      HTTPS TCP 443 0.0.0.0/0
        <br />
        <br />
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     HTTPS TCP 443 ::/0
        <br />
        <br />
&nbsp;&nbsp;&nbsp;&nbsp;    f. LAUNCH INSTANCE
    <br />
    <br />
3. Login to EC2 instance
<br />
<br />
4. Command line of Amazon Linux AMI 
<br />
<br />
&nbsp;&nbsp;&nbsp;&nbsp;    a. When server is booted
    <br />
    <br />
 &nbsp;&nbsp;&nbsp;&nbsp;   &nbsp;&nbsp;&nbsp;&nbsp;    sudo su
        <br />
        <br />
 &nbsp;&nbsp;&nbsp;&nbsp;  &nbsp;&nbsp;&nbsp;&nbsp;     yum -y update
        <br />
        <br />
 &nbsp;&nbsp;&nbsp;&nbsp;   &nbsp;&nbsp;&nbsp;&nbsp;    yum install -y aws-cli
        <br />
        <br />
 &nbsp;&nbsp;&nbsp;&nbsp;   &nbsp;&nbsp;&nbsp;&nbsp;    cd /home/ec2-user
        <br />
        <br />
 &nbsp;&nbsp;&nbsp;&nbsp;   b. Here you will setup your AWS access, secret, and region.
    <br />
    <br />
   &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;     aws configure
        <br />
        <br />
    &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;    aws s3 cp s3://aws-codedeploy-us-east-1/latest/install . --region us-east-1 (if in east AWS)
        <br />
        <br />
    &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp; aws s3 cp s3://aws-codedeploy-us-west-2/latest/install . --region us-west-2 (if in west AWS)
        <br />
        <br />
   &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;     chmod +x ./install
        <br />
        <br />
  &nbsp;&nbsp;&nbsp;&nbsp;  c. This is simply a quick hack to get the agent running faster.
    <br />
    <br />
  &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;      sed -i "s/sleep(.*)/sleep(10)/" install
        <br />
        <br />
   &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;     ./install auto
        <br />
        <br />
  &nbsp;&nbsp;&nbsp;&nbsp;  d. Verify it is running.
    <br />
    <br />
   &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;     service codedeploy-agent status

   
