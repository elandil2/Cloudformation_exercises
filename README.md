# CloudFormation Exercise Template

This CloudFormation template is designed for educational exercises and demonstrations related to AWS CloudFormation. It provisions an Amazon EC2 instance with custom user data and associated resources.

## Parameters

- **NameofService**: A parameter for specifying the name of the service. This is a string parameter and is used as a tag for the EC2 instance.

- **InstanceTypeParameter**: A parameter for specifying the EC2 instance type. It has default values and allowed values to choose from.

- **KeyName**: A parameter for specifying the name of an existing EC2 key pair. This key pair is used for SSH access to the EC2 instance.

## Mappings

- **AmiRegionMap**: This mapping defines AMIs (Amazon Machine Images) for different AWS regions. It is used to select the appropriate AMI based on the region.

## Resources

- **WebServer**: This is the main resource and represents the EC2 instance. Here's what it does:
  - It uses the `AWS::CloudFormation::Init` metadata section to define configurations for the EC2 instance. These configurations include packages to install, commands to run, files to create, and services to enable.
  - The `UserData` section contains a shell script that is executed when the instance launches. It installs the AWS CloudFormation tools, runs `cfn-init` and `cfn-signal`, which are used for CloudFormation resource initialization and signaling stack creation completion.
  - The `InstanceType`, `KeyName`, and `ImageId` properties are set based on the specified parameters and mapping.
  - It sets a tag on the instance with the name of the service specified in the `NameofService` parameter.
  - It associates the instance with the `VprofileSG` security group.

- **VprofileSG**: This is an EC2 security group resource that allows inbound traffic on ports 80 (HTTP) and 22 (SSH) from specific IP addresses.

## Outputs

- **PrintSomeInfo**: An output that displays the public DNS name of the EC2 instance.

### Purpose

The purpose of this CloudFormation template is to demonstrate the following concepts:

- Parameter usage: How to define parameters for customizing resource creation.

- Mapping usage: How to define mappings for region-specific resources.

- Resource creation: How to create AWS resources like EC2 instances and security groups.

- Metadata and User Data: How to use metadata and user data to customize EC2 instances during launch.

- Output usage: How to create outputs to retrieve information from the created stack.

This template can be used for educational purposes and as a starting point for more complex CloudFormation stacks.
