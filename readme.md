"Metal Rig" ECS Execution Environment"
======================================
This set of CloudFormation (Cfn) templates creates an execution environment for Twig using pure AWS
"metal" techniques.  That is, no software (other than the AWS CLI) is required to create the environment.

To start your environment:

1. Install the AWS CLI if you don't already have it.  This is not strictly necessary, but the `deployTemplates` script uses it, so unless you want to manually do what the script does ...
1. Create an S3 bucket for the template bundle, in your preferred region.  I find it helpful to give it the eventual name you'll give the Cfn stack.
1. Run `./bin/deployTemplates <s3 bucket name>`.  This bundles the templates and places them in the S3 bucket.
1. Create a Cfn stack referring to the S3 location of the template bundle (the URL is output from the script).  Provide reasonable parameters (most have reasonable defaults).
1. Once the stack completes, you'll have a VPC running an ECS cluster and a couple of ELBs.  Complete the setup of a build stack in order to deploy to this environment.

