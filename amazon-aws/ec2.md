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

1\) **SSH into Your Linux Box via your key \(.pem\) **

```bash
ssh -i Stable-Current-PublicFE-RestrictedBE.pem ec2-user@ec2-xx-xxx-xx-xx.eu-west-2.compute.amazonaws.com
```

2\) Create a new user that will access the instance and have sudo powers

```bash
sudo useradd -s /bin/bash -m -d /home/bryan  -g root bryan
```

The substring "bryan" in the above command is an arbitrary value which serves as the user's username.  You should replace both  with the username you would like, and of course, both values should be identical.

Here's the breakdown of what's going on here:

* -s /bin/bash : use /bin/bash as the standard shell
* -m -d /home/USERNAME : create a home directory at /home/USERNAME
* -g root : add to group root
* USERNAME : the username of the new user

### Extra Security Measures

These are optional but recommended extra steps to lock down your server and stymie would be hacker kiddies.

#### Change Your SSH Port from Default 22

1. Launch and connect to EC2 instance running Amazon Linux.
2. Promote to root and edit /etc/ssh/sshd\_config
3. Edit line 17 \(usually 17\) \#port 22. You'll need to un-comment the line and change the port to whatever you like. Example: port 2222
4. Save changes and exit
5. Restart sshd, `$/etc/init.d/sshd restart`
6. Make sure the new port is added to the INBOUND rules for your security group. The example above I would add a new TCP connection for 2222 for 0.0.0.0/0, after testing is over I would then lock down the source address to something more specific. 

### Kill the Default EC2-USER User

Hacker kiddies likely know about the **ec2-user **profile so now that we have a new user that can access and has full control, we can "kill" the default user so that if a hacker kiddie gets the bright idea to try and access SSH via the default known user, it will run into a brick wall and feel sad.

## High End Graphics Boxes

When you need to run graphic intensive apps like games or do stuff like editing multimedia \(video, etc\) you are best creating a high-end graphics box that you can use sparingly as needed \(they are expensive\).  Here is my setup resources:

### Windows Server 2012 R2 with NVIDIA / HMV Instance

That's a mouthful, but essentially this article does a lot of the overview explanation:

[http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/accelerated-computing-instances.html](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/accelerated-computing-instances.html)

As per above:

> If you require high processing capability, you'll benefit from using accelerated computing instances, which provide access to hardware-based compute accelerators such as Graphics Processing Units \(GPUs\) or Field Programmable Gate Arrays \(FPGAs\). Accelerated computing instances enable more parallelism for higher throughput on compute-intensive workloads.
>
> GPU-based instances provide access to NVIDIA GPUs with thousands of compute cores. You can use GPU-based accelerated computing instances to accelerate scientific, engineering, and rendering applications by leveraging the CUDA or Open Computing Language \(OpenCL\) parallel computing frameworks. You can also use them for graphics applications, including game streaming, 3-D application streaming, and other graphics workloads.

Recommended Instance:

https://aws.amazon.com/marketplace/pp/B00SK9DXLG?qid=1495755634594&sr=0-4&ref\_=srh\_res\_product\_title 

Your subscriptions:

https://aws.amazon.com/marketplace/library























