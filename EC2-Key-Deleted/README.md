# How to Get authorized_keys(public Key) Back and Login to EC2 Server

## Step 1: Lets Delete the authorized_keys
    > ssh -i Shivam.pem ubuntu@77.95.5.10
    > cd ~/.ssh/
    > ls 
    authroized_keys 
    > rm authorized_keys

## Step 2: Go to AWS IAM Role and Create a Role
    name - AmazonSSMManagedInstanceCore
    policy - AmazonSSMManagedInstanceCore

## Step 3: Now Go to Amazon running Instance
    > Click on Action > Click on Security > Click on Modify IAM Role
    > Attach the Policy the You Created - (AmazonSSMManagedInstanceCore)

## Step 4: Generate Private Key Using Existing Public Key inside Local Laptop
    > ssh-keygen -y -f Shivay-office.pem

    > you will get private key copy that

## Step 5: Connect to Instance using AWS SSM(System Manager)
    Clikc on Instance > Click connect > Click on Session Manager 
    > sudo mkdir -p /home/ubuntu/.ssh
    > sudo chmod 700 /home/ubuntu/.sshsudo chmod 700 /home/ubuntu/.ssh$
    > echo "paste_the_generated_private_Key" | sudo tee /home/ubuntu/.ssh/authorized_keys

> ***Fix the Owner Ship Permission*** 

    > sudo chown -R ubuntu:ubuntu /home/ubuntu/.ssh
    > sudo chmod 600 /home/ubuntu/.ssh/authorized_keys

## Step 6: Good to Go Now try to Connect from your Local 
     ssh -i Shivay-office.pem ubuntu@98.86.166.59

- All Set 