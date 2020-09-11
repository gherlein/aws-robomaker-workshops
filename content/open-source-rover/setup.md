---
title: "Prep: Workshop Setup"
chapter: true
weight: 1
description: "We will start by setting up your AWS account to develop robot applications with AWS RoboMaker."
---

# Workshop Setup

Before we get started learning about robot development, we need to configure a few things.  This workshop can be completed in two ways:  at a public event where AWS provides temporary AWS accounts; or on your own, where you use your own AWS account.

Are you completing this workshop at a public event or training session, **and** have you have been provided with a 12-character workshop code?


   <button class="ui-button" onclick="document.getElementById('with_code').style.display = 'block';document.getElementById('no_code').style.display = 'none';">**Yes, I have a code**</button>&nbsp;&nbsp;<button class="ui-button" onclick="document.getElementById('with_code').style.display = 'none';document.getElementById('no_code').style.display = 'block';">**No.  I will use my own AWS account.**</button>

<div id="with_code" style="display:none">

{{% md %}}
### Log  in to the AWS Console and set the AWS Region

For this workshop, we've created temporary AWS accounts for all attendees.  You were provided with a code to access your AWS account for the workshop.  You will need that code in the next steps.  To get started, enter the AWS Console by going to this web site:

**[https://dashboard.eventengine.run](https://dashboard.eventengine.run)**   

On the *Who are you?* form, enter the code you were provided (ensure the case is correct) and click **Proceed**.

![Event Engine Login](../../images/open-source-rover/event-engine-login.jpg)

Then click on the **AWS Console** button, and then the **Open Console** button on the pop-up.

![Event Engine Open Console](../../images/open-source-rover/event-engine-open-console.jpg)

The default is US West (Oregon) region for this workshop, however, feel free to select a different region.

![Region selection](../../images/open-source-rover/region-selection.jpg)

### Launch CloudFormation Stack 
AWS CloudFormation provides a common language to describe and provision infrastructure resources in your cloud environment. CloudFormation allows you to use a simple text file to model and provision the resources needed for the workshop.  For this workshop, we've pre-created a template that simplifies some of the setup.  The infrastructure it creates is needed to run the activities.  It will create an S3 bucket and networking resources.

Once you have successfully signed into the AWS console, click the button below to launch a CloudFormation stack to create the required resources:

[![Launch Stack](../../images/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?templateURL=https://s3.amazonaws.com/assets.robomakerworkshops.com/cfn/bootstrap.rover.no-roles.cfn.yaml)

1. On the *Create stack* page, accept the defaults and click **Next**.
2. On the *Specify stack details* page, set *Stack name* to a value that will help you identify this stack, such as "reMARS-workshop".
3. In the *Parameters* section, the networking configuration has been pre-populated.  Leave the default values.
4. For the *s3BucketName* field, the value must be globally-unique, and it must be lower case and not include any special characters (only '.' or '-').  This is because it will be used in the domain name for the S3 bucket that gets created.  For today's workshop, namespace your bucket with your initials or a user name to improve its uniqueness.  For example, if your name is Jane Penelope Smith, you might name the bucket, "jps-remars-workshop".  Click **Next**.
5. On the *Configure stack options* page, use the default values and click **Next**.
6. On the *Review* page, review the choices, and click **Create stack**.


This will create:

- a **VPC** with a pair of **subnets** and a **default security group** to run AWS RoboMaker instances in.
- an **S3 bucket** to store your RoboMaker assets (such as the packaged robot application).

The stack creation should only take a minute or two.  Once the status has changed to CREATE_COMPLETE, click on the stack's  **Outputs** tab. It will provide you with several Key/Value pairs that we will use later in the workshop.  Specifically, you should copy and paste several Key/Values to a notepad application.  This is not required, but be prepared to navigate back to the CloudFormation **Outputs** tab when you're asked for these values later.  You will need the values for the following:

- VPC
- PublicSubnet1
- PublicSubnet2
- DefaultSecurityGroupID
- RoboMakerS3Bucket

**Congratulations!** You have completed the setup portion of the workshop.

**[Continue to the next module.](../marsrover/)**
{{% /md %}}
</div>

<div id="no_code" style="display:none">
{{% md %}}
### Log  in to the AWS Console and set the AWS Region

When using your own AWS account to complete this workshop, your user need read and write permissions to several services, including AWS RoboMaker, Amazon S3, AWS Cloud9, and Amazon CloudWatch.

### Launch CloudFormation Stack 
AWS CloudFormation provides a common language to describe and provision infrastructure resources in your cloud environment. CloudFormation allows you to use a simple text file to model and provision the resources needed for the workshop.  For this workshop, we've pre-created a template that simplifies some of the setup.  The infrastructure it creates is needed to run the activities.  It will create an S3 bucket, networking resources, and it will create roles in your account that give AWS RoboMaker the permissions it needs to run the simulations.

Once you have successfully signed into the AWS console, click the button below to launch a CloudFormation stack to create the required resources:

[![Launch Stack](../../images/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?templateURL=https://s3.amazonaws.com/assets.robomakerworkshops.com/cfn/bootstrap.rover.cfn.yaml)

1. On the *Create stack* page, accept the defaults and click **Next**.
2. On the *Specify stack details* page, set *Stack name* to a value that will help you identify this stack, such as "reMARS-robot-workshop-resources".
3. In the *Parameters* section, the networking configuration has been pre-populated.  Leave the default values.
4. For the *s3BucketName* field, the value must be globally-unique, and it must be lower case.  This is because it will be used in the domain name for the S3 bucket that gets created.  For today's workshop, namespace your bucket with your initials or a user name to improve its uniqueness.  For example, if your name is Jane Penelope Smith, you might name the bucket, "jps-remars-workshop".  Click **Next**.
5. On the *Configure stack options* page, use the default values and click **Next**.
6. On the *Review* page, review the choices, and check the box at the bottom of the page to "acknowledge that AWS CloudFormation might create IAM resources with custom names".
7. Click **Create stack**.


This will create:

- a **VPC** with a pair of **subnets** and a **default security group** to run AWS RoboMaker instances in.
- an **S3 bucket** to store your RoboMaker assets (such as the packaged robot application).

The stack creation should only take a minute or two.  Once the status has changed to CREATE_COMPLETE, click on the stack's  **Outputs** tab. It will provide you with several Key/Value pairs that we will use later in the workshop.  Specifically, you should copy and paste several Key/Values to a notepad application.  This is not required, but be prepared to navigate back to the CloudFormation **Outputs** tab when you're asked for these values later.  You will need the values for the following:

- VPC
- PublicSubnet1
- PublicSubnet2
- DefaultSecurityGroupID
- RoboMakerS3Bucket

**Congratulations!** You have completed the setup portion of the workshop.

**[Continue to the next module.](../marsrover/)**
{{% /md %}}

</div>