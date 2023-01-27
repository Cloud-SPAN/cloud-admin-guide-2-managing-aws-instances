---
layout: lesson
root: .
---
The environments and configurations presented in the previous lesson, [Setting Up Your Cloud and Linux Environments](https://cloud-span.github.io/cloud-admin-guide-1-setting-work-environments/), comprise a **base development environment** to create and manage AWS services with both the AWS Console and the AWS CLI (command line interface). If you are using an AWS **personal account** (that you created and configured as described in that lesson), you can create and manage **any service in any AWS region**, as your account was configured with the AdministratorAccess permissions policy which "*Provides full access to AWS services and resources*". 
Towards using the Scripts to create and manage AWS instances, we will first need to configure **Internet access** for the instances. The instances configuration and the Scripts were designed for each instance to be accessed through a **domain name** and with the program `ssh` using an encrypted login key, as outlined below. Hence, we will create a **base domain name** from which the Scripts will create, for each instance, a **subdomain** name to identify and make each instance accessible with `ssh`. Creating a domain name in your AWS account will incur some cost, as low as US $5.00 per year or more depending on the  *suffix /top-level domain* (TLD) that you choose for your base domain name. Examples of TLDs include: `.com`, `.net`, `.org`, `.link` (the cheapest in AWS), among many others. If you already have a domain name in place, you can use that instead. Your account will also incur costs for any service you launch that is not included in the **AWS Free Tier** --- check the lesson [AWS Costs Explained](https://cloud-span.github.io/create-aws-instance-3-costs-explained/) from another Cloud-SPAN course, so you know your free limits. 

If you are using an AWS **institutional account** (that was created and configured by the IT department in your institution), you will most likely not be directly responsible for the cost of using a domain name or any other service with your account. However, you may need to ask your IT department to configure a base domain name for you, or to follow some guidelines to specify the domain name. Your account may also have restrictions as to the **AWS region where you can create and manage AWS services**. For instance, the AWS institutionl account of the Cloud-SPAN project can only make use of services in the eu-west-1 Ireland region, and the Cloud-SPAN base domain name was suggested and configured by our IT department. If your institutional account is restricted to use an AWS region other than Ireland, you may need to ask your IT department to make a copy, to your AWS account, of the Amazon Machine Image (**AMI**) template used by the Scripts to create AWS instances. **Your IT department should be able to help you** with this and other matters; just let them know what you need to configure in your AWS account to use the Scripts, and whenever you come accross **Access Denied** or similar messages when using the Scripts.

# Overview
We use the Scripts to create and manage multiple AWS instances for hands-on training purposes. When running a workshop, a number of instances is created from an AMI template that is configured
with ‘omics data and software analysis tools that are relevant to the workshop.  Each student is granted exclusive access to one instance.

Each instance is created to be accessed through a **domain name** using `ssh` and an encrypted login key file. 

For example, using the base domain name of the Cloud-SPAN project, `cloud-span.aws.york.ac.uk`, the (sub) domain name for an instance named `instance001` would be `instance001.cloud-span.aws.york.ac.uk`.

Using the base domain name of an AWS personal account, for example, `awsplaicloud.com`, the domain name for the same instance name would be `instance001.awsplaicloud.com`.

Once an instance is created, the end user will access the instance `csuser` account with `ssh` providing the name of the corresponding login key file as shown below.

Using the AWS Cloud-SPAN institutional account base domain name:
~~~
$ ssh -i login-key-instance001.pem  csuser@instance001.cloud-span.aws.york.ac.uk     ### -i stands for identity file
~~~
{: .bash}

Using the personal account based domain name:
~~~
$ ssh -i login-key-instance001.pem  csuser@instance001.awsplaicloud.com              
~~~
{: .bash}

Each instance domain name is mapped to an IP address. Domain names, IP addresses, and login keys are created *automatically* on creating the corresponding instances, and deleted likewise when the corresponding instances are deleted.

### Configure Instances Internet Access

Episode 1 will guide you to configure internet access for the instances you will create with the Scripts. This involves:
- creating a base domain name 
- creating a few access rules for the communication ports used by the `ssh` program
- selecting an AWS network to which the instances will be attached so that they can be reached from anywhere with `ssh`.

 <!-- this reference is to a section in a another page file is right -- don't delete [Create a Base Domain Name](01-configure-instances-internet-access#1-create-a-base-domain-name). -->
### Instances Management Tasks Using the Scripts

Episode 2 is the guide for using the Scripts to create and manage multiple instances for a course/workshop. The episode shows:
- how to configure the Scripts with the names of the instances to create and the AWS resources to use (base domain name, AMI template, etc.).
- how to organise the Scripts configuration files for multiple courses. 
- how to use/run the Scripts and manage unforseen instances management requests such as cancellations by workshop participants.
- some troubleshooting

### AMIs Management

Episode 3 is about managing Amazon Machine Images (AMIs). AWS instances are copies (instances) of an AMI. When you use the Scripts to create AWS instances for a course, you must specify from which AMI to make the copies.

You need to create a new AMI if the software or data used in a course change, but there are other reasons that may require creating a new AMI.

The episode presents the management of AMIs that we do as part of managing AWS instances with the Scripts.

### The Scripts Design and Management Tasks

In construction. 