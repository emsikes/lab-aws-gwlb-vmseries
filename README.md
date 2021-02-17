# PS Regional Training 2021 AWS Labs


<img src="https://www.paloaltonetworks.com/content/dam/pan/en_US/images/logos/brand/primary-company-logo/Parent-logo.png" width=50% height=50%>

## Overview

This lab will involve deploying a solution for AWS using Palo Alto Networks VM-Series in the Gateway Load Balancer (GWLB) topology.


## Deployment





### Step x: Update IAM Policies


<img src="https://user-images.githubusercontent.com/43679669/108144448-aa08ad00-7097-11eb-926d-66ab34e050da.png" width=50% height=50%>




### Step x: Launch CloudShell

- Check which Marketplace VM-Series images (AMIs) are available

This terraform deployment will look up the AMI ID to use for the deployment based on the variable `fw_version`. New AMIs are not always published for each minor release. Therefore, it is a good idea to verify what version AMI most closely matches your target version.

In cloud console, enter:

`aws ec2 describe-images --filters "Name=owner-alias,Values=aws-marketplace" --filters Name=name,Values=PA-VM-AWS-10* Name=product-code,Values=6njl1pau431dv1qxipg63mvah --region us-west-2`

How many different BYOL AMIs are avilable for 10.x in this region?

product-code is a global value that correlates with Palo Alto Networks marketplace offerings. This is global and the same across all regions. There will be changes to this as vm-flex offerings come live.

```
    "byol"  = "6njl1pau431dv1qxipg63mvah"
    "payg1" = "6kxdw3bbmdeda3o6i1ggqt4km"
    "payg2" = "806j2of0qy5osgjjixq9gqc6g"
```
The name tag of the image should be standard and can be used for the filter. For example `PA-VM-AWS-9.1*`, `PA-VM-AWS-9.1.3*`, `PA-VM-AWS-10*`. This is the same logic the terraform will use to lookup the AMI based on the `fw_version` variable.

**We see that 10.0.4 AMI is availble, so we will use that for the variable**


- Generate SSH Key

Any EC2 Instance must be associated with a SSH keypair, which is the default method of initial interactive login to instances. With successful bootstrapping, there should not be any need to connect to the VM-Series instances direclty with this key, but it is usually good to keep this key securely stored for any emergency backdoor access. For this lab, a keypair will be generated in the cloudshell and then terraform will create a corresponding object in AWS using the same key.

`ssh-keygen -f ~/.ssh/ps-lab -t rsa -C ps-lab`




### Step x: Clone the Repository

```
$ git clone https://github.com/PaloAltoNetworks/ps-regional-2021-aws-labs.git
```


text to be copied to clip board goes here

### Step 50: Finished

Congratulations!

You have now successfully ….


Manual Last Updated: 2021-02-16
Lab Last Tested: -

