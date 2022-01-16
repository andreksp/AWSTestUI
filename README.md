## UI Deploy (Angular + AWS EC2 + AWS AutoScaling + AWS Pipeline)

## Objective

1) Deploy an Angular application directly EFS
2) Use AWS Code Pipeline to build and deploy the files on EFS directly
3) Create an auto Scaling feature and boot strap script
4) Based on this article: https://blog.shikisoft.com/deploy-to-amazon-efs-with-aws-codebuild-codepipeline/

## Configurations

1) Create EFS
2) Network
   1) Create a private subnet. (Simple Subnet)
   2) Create a routing table a associate with the private subnet.
   3) Create a NAT Gateway on public subnet
   4) On the routing table created. add a routing to 0.0.0.0/0 to the Nat gateway created.
3) Create AWS Pipeline with the build in the private sub net.
   1) Add the EFS on the AWS Build
4) Auto Scale Bootstrap Script ( Change the ID of the EFS accordingly)
    #!/bin/bash
    sudo su
    sudo amazon-linux-extras enable nginx1
    sudo yum install nginx -y
    cd /
    mkdir /mnt/efs/
    sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-027d9e36b1c2aec7e.efs.sa-east-1.amazonaws.com:/ /mnt/efs
    cd/
    cd /etc/nginx/
    sed -i 's/usr\/share\/nginx\/html/\mnt\/efs/g' nginx.conf
    sudo systemctl start nginx
