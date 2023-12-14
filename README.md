# AWS CloudWatch to Opsgenie Integration

The included CloudFormation template allows you to integrate CloudWatch with Opsgenie via a secure and encrypted configuration using AWS Secrets Manager. The infrastructure incorporates an SNS topic and subscription, a CloudWatch alarm, and a metric filter to detect and respond to specified log events.

## References

- [Integrate Opsgenie with Amazon CloudWatch](https://support.atlassian.com/opsgenie/docs/integrate-opsgenie-with-amazon-cloudwatch/)

## Prerequisites

Before deploying the template, you'll need:

- An Opsgenie account with API integration enabled.
- An Opsgenie API integration URL, example `https://api.eu.opsgenie.com/v1/json/cloudwatch?apiKey=randomstring`
- The Opsgenie API integration URL stored as a plaintext secret in AWS Secrets Manager.

## Setup

### Creating the Opsgenie API Endpoint Secret

Store the Opsgenie API endpoint URL as a **plaintext** secret in AWS Secrets Manager with the secret name of your choice.

### Forking the Repository

To use and customize this CloudFormation template for your own use:

Just fork this repository. Once the repository has been forked, you can clone your fork to your local machine using:

git clone https://github.com/<username>/cloudwatch-opsgenie-integration.git

Make sure to replace <username> with your actual GitHub username.

Navigate to your cloned repository:

```bash
cd cloudwatch-opsgenie-integration
```

Create a new branch to make your changes:

```bash
git checkout -b my-custom-branch
```

You can now edit the CloudFormation template files to match your necessary configurations for log monitoring and alerting.

### Continuing with the Deployment

After making the necessary changes to your local clone, add, commit, and push your changes to your fork, and then follow the instructions mentioned previously to deploy the CloudFormation stack using the AWS CLI. Here's an example of the Git commands for committing and pushing your changes:

```bash
git add .
git commit -m "Customize template for my environment"
git push origin my-custom-branch
```

From this point on, you can proceed with deploying the CloudFormation stack with your customizations as described in the previous section of the README.

### Deploying the CloudFormation Stack

Navigate to the repository directory:

```bash
cd cloudwatch-opsgenie-integration
```

Review and update the CloudFormation template file (`template.yml`) as per your requirements for log monitoring and alerting.

Deploy the CloudFormation stack, specifying the necessary parameters in `parameters.json`.

Here is an example AWS CLI command to get you started:

```bash
aws cloudformation create-stack \
    --stack-name CloudWatchOpsgenieIntegrationStack \
    --template-body file://template.yml \
    --parameter-overrides file://parameters.json"
```

Replace parameter values (e.g., `MyOpsgenieEndpointSecret`, `MyAppLogs`, etc.) with your specific configurations.

Monitor the stack creation process in the AWS CloudFormation console to ensure successful deployment.

Once the stack is created, CloudWatch will monitor the specified logs and, upon alarm conditions, will notify the configured Opsgenie endpoint.
