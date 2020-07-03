---
layout: default
categories: [lab]
tags: [lab0]
excerpt_separator: <!--more-->
permalink: /lab/lab-0
name: /lab/lab-0.html
---

# Lab 0 - Setup the Labs

The following Setup Guide is designed to help you get up and running quickly for the workshop.

For this, we will be using [AWS Cloud9 Development ](https://aws.amazon.com/cloud9/) environment. AWS Cloud9 is a cloud development IDE that we will use to compile and build our Amazon FreeRTOS code.

Once you have setup the environment, you will be able to build and  compile the different labs, you will download the binary compiled  firmware files, and you will flash your device locally on your laptop.


## Create Cloud9 Environment

Log in to your [AWS Account Console](https://console.aws.amazon.com) and search for Cloud9

![Search for Cloud9](images/lab0/c9-00-search.png)

Create a New Environment by clicking the **Create Environment** button

![Create the Cloud9 env](images/lab0/c9-01-create-env.png)

Name your environment and provide a description, then press **Next step**

**Warning** If you are running  this workshop within the same account as other people, please make sure  to name your environment with a customized name of your choosing in  order to find your environment. Why not your name?

![Start cloud9](images/lab0/cloud9-name.png)

Now configure your Cloud9 instance:

- For Environment type, choose **Create a new instance for environment (EC2)**
- Choose **t2.micro** for the instance type
- Choose **Ubuntu Linux** for the Platform
- Press **Next step**

![Configure the Cloud9 env](images/lab0/cloud9-config.png)

- Review and press **Create environment**

![Review the Cloud9 env](images/lab0/cloud9-review.png)

## Done


You are done with the IDE setup and are ready to move to [Lab 1]({{ "/lab/lab-1" | absolute_url }})