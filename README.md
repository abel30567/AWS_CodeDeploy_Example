# AWS_CodeDeploy_Example
1. Create IAM Roles
<br />
CodeDeploy & EC2CodeDeploy

2. Create EC2 instance with following categories
<br />
    a. Choose AMI: Amazon Linux AMI
    <br />
    b. Choose Instance type: t2.micro
    <br />
    c. Configure Instance: Choose EC2CodeDeploy IAM role
    <br />
    d. Tag Instance: Name it what you please
    <br />
    e. Configure Security Group: 
    <br />
        HTTP TCP 80 0.0.0.0/0
        <br />
        HTTP TCP 80 ::/0
        <br />
        SSH TCP 22 <YOUR IP ADDRESS>
        <br />
        HTTPS TCP 443 0.0.0.0/0
        <br />
        HTTPS TCP 443 ::/0
        <br />
    f. LAUNCH INSTANCE
    <br />
3. Login to EC2 instance
<br />
4. Command line of Amazon Linux AMI 
<br />
    a. When server is booted
    <br />
        sudo su
        <br />
        yum -y update
        <br />
        yum install -y aws-cli
        <br />
        cd /home/ec2-user
        <br />
    b. Here you will setup your AWS access, secret, and region.
    <br />
        aws configure
        <br />
        aws s3 cp s3://aws-codedeploy-us-east-1/latest/install . --region us-east-1
        <br />
        chmod +x ./install
        <br />
    c. This is simply a quick hack to get the agent running faster.
    <br />
        sed -i "s/sleep(.*)/sleep(10)/" install
        <br />
        ./install auto
        <br />
    d. Verify it is running.
    <br />
        service codedeploy-agent status
