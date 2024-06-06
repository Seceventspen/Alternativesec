---
layout: post
title: 'Kali in the Cloud: Automated Deployment'
tags: [Pentest, AWS, Kali]
featured_image_thumbnail: assets/images/posts/aws-kali/aws-kali-CF-logo.png
featured_image: assets/images/posts/aws-kali/aws-kali-CF-logo.png
featured: true
hidden: true
---

This blog post will talk through the setup and deployment of a Kali Linux EC2 using AWS CloudFormation.

Basically, I got tired of doing the same thing over and over, and decided to make my life easier, sorry, more efficient, and automate the build task of something I do regularly.

<!--more-->

## What is AWS Cloud Formation?

AWS CloudFormation is a service that helps you model and set up your AWS resources so that you can spend less time managing those resources and more time focusing on your applications that run in AWS. You create a template that describes all the AWS resources that you want (like Amazon EC2 instances or Amazon RDS DB instances), and CloudFormation takes care of provisioning and configuring those resources for you. You don't need to individually create and configure AWS resources and figure out what's dependent on what; CloudFormation handles that. The following scenarios demonstrate how CloudFormation can help.

[CloudFormation References Docs](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)

## Getting Started ...

Ok, so before we get started, let me clarify a couple of things about this blog post:

What this post is **not**:

- This is not going to be a complete end to end walkthrough / set-up guide
	- AWS understanding and knowledge is pre-assumed. If you're new to AWS and Cloud Formation you might need to read up elsewhere then come back here.
- This is not a best practice on how to write a `YAML` config file for AWS Cloud Formation
	- For me it works and does what I need it to do.

What this post **is**:

- It's providing a resource which **may** aid **YOU**, in speeding up your productivity, in relation to building tooling/capabilities.

***Note:** Automation can increase productivity, because automation tools can perform tasks faster and around the clock, allowing more to be done within a certain timeframe. In addition, instead of these repetitive tasks, us humans can perform non-automated tasks in parallel, increasing productivity even more.*

What you'll **need**:

- A credit card or access to one _(this is an AWS requirement, not mine lol)_
	- Obviously only use one you are legally entitled/authorised to do so.
- An [AWS](https://signin.aws.amazon.com/) account or access to an AWS account.
- Correct [IAM](https://aws.amazon.com/iam/) privileges to enable using:
	- Creating/deploying an EC2 instance
	- The AMI Market place
	- Cloud Formation 

Right ... now it's time to deploy a computer on someone else's server, e.g., the AWS cloud!

# Instructions

## AWS Kali EC2 Build and Cloud Formation Template

### (1) My AWS Kali Cloud Formation Template

You can grab the AWS Kali Cloud Formation Template below:

- `master-kali-ec2-instance.yaml`

```yaml
AWSTemplateFormatVersion: '2010-09-09' # Do not change this line
Description: Create an EC2 instance with Kali Linux AMI, t2.micro, and SSH inbound access in your chosen VPC.

Resources:
  CustomSSH:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Security group for EC2 instance
      VpcId: vpc-XXXXXXX # Add your AWS VPCId here - do not change
      SecurityGroupIngress:
        - CidrIp: xx.xx.xx.xx/32  # Replace with your desired IP address
          IpProtocol: tcp
          FromPort: 22
          ToPort: 22
        - CidrIp: xx.xx.xx.xx/32 # Optional VPN IP address
          IpProtocol: tcp
          FromPort: 22
          ToPort: 22

  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro # Instance size - Although t2.medium is recommended, only swap to it if needed
      SecurityGroupIds:
        - !Ref CustomSSH # Custom sec group name
      SubnetId: subnet-XXXXXXXX  # Add your AWS existing VPCId here
      KeyName: your-key-here  # Replace with your SSH key pair name - should already be in the AWS key vault
      ImageId: 
        Fn::FindInMap:
          - AWSRegionArch2AMI
          - Ref: "AWS::Region"
          - AMIKali
      BlockDeviceMappings:
        - DeviceName: /dev/xvda
          Ebs:
            VolumeSize: 30  # Set storage size to 30GB, change to suit
      UserData:
        Fn::Base64: |
            #!/bin/bash -xe
            echo "h3llo haxXor"
            sudo su
            apt update && apt upgrade -y
            DEBIAN_FRONTEND=noninteractive apt install kali-linux-headless -y -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold"
            apt install seclists -y
            echo " mi$chi3f m@nag3d"

      Tags:
        - Key: Name
          Value: xxxxxx-Custom-Kali # Your custom name here
        - Key: OS
          Value: Kali Linux
        - Key: OwnerContact
          Value: "@xxxxx" # Enter your name here

Mappings:
  AWSRegionArch2AMI:
    us-east-1:
      AMIKali: ami-0eb546bea6ed49174  # Check this is still the latest version, if not replace with the latest Kali Linux AMI ID for us-east-1

Outputs:
  InstanceId:
    Description: Instance ID of the newly created EC2 instance
    Value: !Ref MyEC2Instance
```

Some of you may have already spotted the `bash` script included in the `YAML` config. I'll say it now:

- Never, ever run scripts from the internet that you don't understand/are unsure of the outcome!!!

However, here's a quick synopsis of what the `Bash` script does:

1. **Shebang and Debugging**: The script starts with `#!/bin/bash -xe`, which indicates that it's a bash script (`#!/bin/bash`) and enables debugging mode (`-x`) to display each command before it is executed and to exit immediately if any command returns a non-zero status (`-e`). This can be useful for troubleshooting and ensuring the script behaves as expected.
    
2. **Echo Command**: The script echoes the string "h3llo haxXor" to the terminal. This is just a playful message and can be deleted/altered as required.
    
3. **Switch to Root User**: The script then attempts to switch to the root user using `sudo su`; however, it's worth noting that using `sudo su` interactively in a script is generally not recommended due to security concerns and potential issues with command execution. You have been warned!
    
4. **Package Management**: The script updates the package repositories (`apt update`) and upgrades installed packages (`apt upgrade -y`). This ensures that the system is up to date with the latest security patches and software updates.
    
5. **Installation of Kali Linux Packages**: Next, the script installs the `kali-linux-headless` package using `apt install` with various options (`-y`, `-o Dpkg::Options::="--force-confdef"`, `-o Dpkg::Options::="--force-confold"`) to automate the installation process and handle configuration file conflicts non-interactively.  Basically you can go grab a coffee, while CF is doing its thing!
    
6. **Installation of SecLists**: Additionally, the script installs the `seclists` package using `apt install -y`. SecLists is a collection of multiple types of lists used during security assessments, such as fuzzing, payloads, and usernames. This further indicates that the script is likely setting up a security-related environment.
    
7. **Final Echo Command**: Finally, the script echoes the string "mi$chi3f m@nag3d" to the terminal. Similar to the first echo command, this is just a playful message and can be deleted/altereded as required.

Assuming that you have, read & understood the `YAML` config, understand what the `bash` script is doing, the overall outcome, you can save the above `YAML` to a file and name something relevant to you.

Now we'll do a check on what the version of the Kali AMI is, then we can add those details into the template, to ensure it matches the current version of the AWS Marketplace AMI for Kali Linux. This can be done by:

```
aws ec2 describe-images --filters "Name=name,Values=kali-last*" "Name=is-public,Values=true" --query 'sort_by(Images, &CreationDate | reverse(@))[].{Name: Name, ImageId: ImageId, ReleaseDate: CreationDate, tag: Description}''
```

_note: You will need to have the AWS cli installed and configured prior to doing the above, along with the necessary IAM privileges._

Assuming that you have the AWS CLI already setup, the correct access rights (IAM), you should see something that looks like this:

```
[
    {
        "Name": "kali-last-snapshot-amd64-2023.3.0-804fcc46-63fc-4eb6-85a1-50e66d6c7215",
        "ImageId": "ami-0eb546bea6ed49174",
        "ReleaseDate": "2023-08-23T15:19:04.000Z",
        "tag": "Kali Linux kali-last-snapshot (2023.3.0)"
    },
    {
        "Name": "kali-last-snapshot-amd64-2023.2.0-804fcc46-63fc-4eb6-85a1-50e66d6c7215",
        "ImageId": "ami-09082a509a1e43235",
        "ReleaseDate": "2023-05-30T21:42:44.000Z",
        "tag": "Kali Linux kali-last-snapshot (2023.2.0)"
    }
]
```

*Note: this output is a little outdated now, but you get the picture of the expected output*

Once you have done the above, complete the next steps prior to heading over to the Cloud Formation page.

Update the following lines in the `YAML` file you have just saved:

- **Line 09**: CidrIp: xx.xx.xx.xx/32
	- Replace with your desired IP address if you want standalone external access outside of the AWS console 
- **Line 27**: KeyName: your-key-here
	- Replace with your SSH key pair name - should already be in the AWS key vault
	- If you dont, you'll need to create one first, see [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/create-key-pairs.html) for details
- **Line 49**: Value: xxxxxx-Custom-Kali 
	- Your custom name here, replace the 'xxxx'
- **Line 53**: Value: "@xxxxx"
	- Enter your name here, replace the 'xxxx'

### (2) AWS Cloud Formation Page

Now that you have the template, verified the Kali AMI ID and updated the lines in the config mentioned above, you can now head over to the AWS Cloud Formation page:

[Coudformation Home Page](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/)

_Note: you'll need to already be logged in_

Then its as simple as:

- Create Stack with new resources (standard)
- 'Template is ready' radio button should already be checked
- Check the ' Upload a template file'
- select the 'Choose file' option
- Select the 'yourname-kali-ec2-instance.yaml' file
- Select 'Next'
- Create a 'Stack' name (pick something relevant/specific to you)
- Select 'Next', 'Next' and finally 'Submit'

### (3) AWS EC2 Dashboard

Now head back to the 'EC2 Dashboard' and look for you EC2 instance name. Then sit back and wait about 15mins or so for everything to initiate, build and finalise.

Upon completion, you should now have:

- a t2.mcrio EC2 Kali Instance within your VPC in us-east-1
- 30gb of storage
- 2 x custom SSH inbound rules
- Kali Linux headless toolset (see the link below for more details)
- SecLists repo installed

Cheers Easy!!!

### [!] Useful/Trouble Shooting Tips

Check Instance Logs: After the EC2 instance has launched, you can check the instance logs to see if there are any errors or issues during script execution. You can access the instance logs using AWS Systems Manager (SSM) or by connecting to the instance and examining the following files:

- `/var/log/cloud-init.log`
- `/var/log/cloud-init-output.log file`

Cloud-Init Status: CloudFormation uses Cloud-Init to execute user data scripts. You can check the status of Cloud-Init by examining the `/var/lib/cloud/instance/boot-finished` file. It should contain the word BOOTFINISHED when Cloud-Init has completed its tasks.

If you want to alter the Kali packages being installed via the bash script in the template, consult here for additional options:

**Kali Meta Packages**

- https://www.kali.org/docs/general-use/metapackages

Current install is `Kali-linux-headless`

- `https://www.kali.org/tools/kali-meta/#kali-linux-headless`
    - note: this should be more than enough for anyone's needs when using kali without a desktop/GUI environment

### [!] Additional Setup/Configurations Tips

Here are some additional steps you might want to consider taking, once CF has finished building your Kali instance for you:

- Change the hostname
- Set the time zone
- Change the keyboard layout
- Installing a GUI on Kali Linux
- Install additional tooling
	- Though the existing bash script could be amended to do this ...

## In Closing

Today, we've discussed and talked through the setup and deployment of a Kali Linux EC2 using AWS CloudFormation.

Knowledge is pre-assumed with respect to AWS, EC2's, IAM, `YAML`, `BASH` and understanding the what the config file does. If you are still unsure you should read up on any of the areas you may be unsure about prior to using any of the resources outlined within this blog post.

**Remember to use this resource/environment responsibly and within legal boundaries.** 

Unauthorized activity in AWS carries severe consequences, including account termination and legal action from AWS for violating terms and conditions. Victims of any malicious activity may seek civil damages for financial losses and punitive damages to prevent future attacks. Perpetrators may face criminal charges, such as computer fraud, identity theft, and unauthorized access to a computer system. You have been warned!

**Lastly,** never run scripts, configs and/or code from the internet that you do not understand! Use at your own risk! You have been warned! 

Thanks for reading!