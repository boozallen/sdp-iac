--------------------------------------------------------
SDP Infrastructure as Code for an AWS Public Environment
--------------------------------------------------------


Infrastructure as Code for deploying the Solutions Delivery Platform on the AWS ECS hosted platform. 

Prerequisite Requirements:
-   The AWS user account running the templates must have appropriate IAM credentials.
-   The AWS account must have a service limit which can accomodate the resources created by the templates.
-   An EC2 Keypair must exist on the account prior to running the templates.
-   Jenkins Master, Agent, and Sobarqube images must be pushed to a repository and referenced in
    their respective templates.