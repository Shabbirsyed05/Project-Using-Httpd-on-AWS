## Deploying a HTTPD Application on AWS EC2

## How i pushed the code to github
1. Initializing git
```
git init
```
2. Moved the files here and performed git add
```
git add .
```
4. Git commit
```
git commit -m "added the files locally"
```
5. Add remotely
```
git remote add origin https://github.com/Shabbirsyed05/Using-Httpd-on-AWS.git
```
6. Push the code . (origin default value and main is the branch.We can keep any branch after creating it)
```
git push -u origin main
```
Above code can be written as 
- git push -u origin main
- git push --set-upsream origin main
- git push -u origin new_brach_name_after_creation

### Set up an AWS EC2 instance

1. Create an IAM user & login to your AWS Console(Administrator access) or it can logined as root but not recommended 
    - Access Type - Password
    - Permissions - Admin
2. Create an EC2 instance
    - Select an OS image - Redhat
    - Create a new key pair & download `.pem` file
    - Instance type - t2.micro
3. Connecting to the instance using ssh
```
ssh -i instance.pem ec2-user@<IP_ADDRESS>
```


### Configuring Redhat on remote VM

1. Updating the outdated packages and dependencies
```
sudo yum update -y
```
2. Install git
```
sudo yum install git -y
```

### Deploying the project on AWS

1. Clone this project in the remote VM
```
git clone https://github.com/Shabbirsyed05/Using-Httpd-on-AWS.git
```
2. Install httpd
```
sudo yum install httpd
```
3. Copy the files to /var/lib/html
```
cp index.html /var/lib/html
cp -r assests/ /var/lib/html
cp -r error/ /var/lib/html
cp -r images/ /var/lib/html
```

4. Go to /var/lib/html path and check the files
```
cd /var/lib/html
pwd
ls
```

5.Start the httpd Service
```
systemctl start httpd
```
6. Forwarding request to httpd for checking its working or not
```
chkconfig httpd
```
7. copy the Public_ip address from the AWS and paste it in to the chrome browser

### Project is deployed on AWS 🎉
   
