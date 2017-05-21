# Amazon EC2

---

This portion of the guide covers the Amazon EC2 service, Amazon's computing service that can provide you with a server infrastructure for any kind of development project that requires a   environment.  You can create server instances on various platforms such as Amazon Linux AMI, Windows, various other Linux distros such as Ubuntu or Redhat and so on.

Let's jump into the fun shall

## SSH Into Amazon Linux Server

SSH allows you to access your server without connecting to it through something like RDP \(remote desktop\).  There are a few different ways that you can gain access via SSH: an ssh key or via username/password authentication.

### SSH via Key

When you create your instance, you will be made to select a **security group** and then a key/value pair.  First make sure that your security group has an inbound rule set that allows connections on port 22.  You will also need to provide the **IP address** from which you will be accessing it in order to increase security.  That way not just any old neck beard can SSH into your box.  EC2 will also then provide with a download of an ssh key in the form of a file with a **.pem extension. **

Open your terminal and then SSH into your Linux box with the following:

`ssh -i /path/to/key.pem ec2-user@{ipv6 address} -p 22`

### SSH via Username / Password

In order to do this, you need to first create a user on your Linux server which you provide with a password and then update a few config files to give the user **sudo power** and then also allow connection to ssh with an authentication credential form that accepts a password.  By default, passwords are not a valid form of authentication for the **SSH daemon**.



