# FortinetAlexa or how to integrate Alexa & Fortinet Security Fabric

The objective is to show you how to integrate Alexa within Fortinet Security Fabric, thanks to Rest API features available on FortiOS and FortiEMS. 

This use case is build to demonstrate how to get information from FortiGate devices (such as memory, cpu and security rating score), plus interact with FortiEMS to gather user informartion and put it into quarantine, avoiding infection in the network. Just with our voice!!

## Requirements:
- Alexa Developer account, in order to create an skill (or program for Alexa).
- AWS account and AWS Lambda function.
- FortiGate VM or Appliance running 6.2.x.
- FortiEMS system running 6.0.x.
- And of course, an Alexa device :)
  
## How it works:
Every time that we do questions or an order to Alexa device, an intent has been executed calling an AWS Lambda section into out function. Every section can do different things, like put in quarantine an user, get information from FG, etc... Remember that the information regarding API is on fndn.fortinet.net website.


## Step-by-step

### 0. Before to start:
 - Create a REST API user in FG and FEMS.
 - Https has to be allowed in remote devices and reachable by AWS.

### 1. Alexa Skill
 - Register on https://developer.amazon.com/ website.
 - Create a new skill and configure:
 	* Name: Public skill name
 	* Languague. It's very important!
 	* Let by default the model and method selected (Custom + Provision your own).
 - Go to JSON editor and copy-paste the content of "AlexaSkillJSON" file.
 - Click on Endpoint tab (left menu), select AWS Lamdba ARN, and copy to skill id.

### 2. AWS console
 - Download the AWSLambdaCodeForUpload.zip file, and change XXXXX values for your env, in code.py file. Zip again.
 - Access to the AWS console.
 - Create a new Lambda function from scratch, selecting Python 3.6.
 - Click on "trigger" symbol and select Alexa Skill Kit, pasting your skill id (from step 1). 
 Info: There is not necessary to add a "destination" object.
 - Into the function code, select "load a zip file" in the "Select entry code" list. Upload your AWSLambdaCodeForUpload.zip file.

### 3. Enjoy
 - Your skill is not "public" at this stage, so it's only possible to access to it through your Alexa user account.
 - Test, fail, test, fail and enjoy.
