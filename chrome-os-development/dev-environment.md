# Chrome OS Development Environment 

If you want to become a Badass \(with a capital B\) developer while honing your skills on a Chromebook, this is the guide for you.  Looking for a good, inexpensive Chromebook? I highly recommend the Acer Chromebook 15.  It's about $300 and is very reliable.  That said, if you are already rocking a Chromebook, then you can jump right in.  This is my personal setup.  There are several different approaches you can take so this is not the only way to do it, but it's a damn good way to do if you want to be awesome like me.  Don't you want to be awesome like me?

Thought so, so let's get right to it then shall we?

## Developer Mode

To be a good Chromebook developer, you are going to need to get your Chromebook into a mode that's made just for developers, and it's oddly called **developer mode.  **I am not sure what Chrome OS engineers were thinking when they named obvious so obviously but my guess is they wanted it to be clear what this particular mode was useful for.  Crazy mofo's, they are.  

There are many guides on this so  Iwon'tw aste my time re-inventing the wheel.  Let's call this a  DRY Gitbook.  Here's one of those:

* https://www.howtogeek.com/210817/how-to-enable-developer-mode-on-your-chromebook/

Now that you have gotten past step 1 \(and if you can't for some reason just quit now\) let's get to the fun.

## Get Yourself a Dev Server

Amazon EC2 gives you what's called a "free tier" for the first year of your account.  This allows you to launch a server instance on any number of platforms \(Linux, Windows, etc\) called a **tiny **instance, which is more than enough to handle your development environment.  

Create an Amazon Linux AMI instance and then check out the following steps:

* Setup your security group to be able to access port 22 and restrict it to your local IP by using the "my IP" option in the dropdown.  Optionally add other custom IP addresses and ranges that can access it should you have several different workstations with different IP's.
* [Create an SSH user that can access your Linux box with a username and password](/amazon-aws/ec2.md "Creating an SSH user with username/password credentials")
* Block the default **ec2-user** user for added security
* Change the ssh port from 22 to some arbitrary port that is open and accepts secure connections
* Login to your Linux box with your new 



