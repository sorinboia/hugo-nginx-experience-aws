+++
title = "Cloud Formation"
date = 2020-07-08T14:37:59+03:00
weight = 20
+++

1. Click the bellow button and deploy the template:

[![Launch Stack](/images/cfls.svg)](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?stackName=NGINX-EKS&templateURL=https://artl-cfn-templates.s3.eu-central-1.amazonaws.com/nginx.yaml)

  
2. Click **Next** 3 times accepting all the defaults, but make sure the following is selected on the last screen:


![CFN IAM Ack](/images/iam-ack.png)


3. Click **Create stack**.

Wait until the **NGINX-EKS** stack Status is **CREATE_COMPLETE**.
