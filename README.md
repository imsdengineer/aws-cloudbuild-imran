# aws-cloudbuild-imran

Why Run Terraform inside AWS Codebuild
Every person in the company can create infrastructure using Terraform, without any configuration in their own laptop.
You can provide a web interface to use Terraform and anyone in the company can create infrastructures
All terraform output logs are saved in Cloudwatch
You can run by schedule
You can run with an hook every time the code changes
You don’t need any infrastructure to run, no EC2 virtual machines no fix cost. You pay only for minutes you use
You can build a small orchestrator running for example a python script before and after the terraform run
Steps for this example
Choose a region, everything will be created in that region

1 - run the cloudformation file
This will create 3 objects:

A codebuild role with administrator access
An S3 bucket where the tfstate file will be saved
A codebuild project that will run the code
2 - run the codebuild to create your terraform environment
To do this this is necessary click on the “Start the build" (blue button) inside codebuild.

This will trigger the creation of the security group in your environment.

Take a look to the CloudWatch logs and verify that everything is green in codebuild

The video for the steps 1 and 2 is this

Run Terraform inside AWS Codebuild part 1/2 creation

3 - destroy the security group running a terraform destroy
click on "Start the build" (Blue button)
Change the destroy variable to True
click on "Start the build" (Blue button)
4 - clean the environment
empty the bucket
delete the cloudformation template