EKS setup with terraform.

Prerecs:
- Administrator access to an aws account. For example, register for a free trial account. 
- Terraform installed
- Awscli installed

1. Create an IAM user

In the AWS console, create an IAM user. Attach the user to a user group. Add the following rights to the user group:
 - AdministratorAccess
 - AmazonEKSClusterPolicy

When the user group is saved, you are provided with Secret Access Key and Access Key ID. *Save these credentials - when you close the window, AWS will never provide the Secret Access Key again!*

In your console, create a ~/.aws repo. Add to it the following two files:

    1. credentials

    [default]
     aws_access_key_id=***********
     aws_secret_access_key=****************************

    2. config

    [default]
     region=eu-west-3

2. run ´´´terraform init´´´. This will initiate terraform and create necessary state files.

3. run terraform plan. This will write out your changes. If something looks off, change the code accordingly.

4. run terraform apply. First, necessary roles, policys and attachments are created for the EKS cluster to talk to the AWS VPC subnets and EC2 container registry. Then, the EKS cluster and node group is created. Cluster creation takes around 10 minutes to complete; the node group takes an additional 10 minutes.

