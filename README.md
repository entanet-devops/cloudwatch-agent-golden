# cloudwatch-agent-golden

## Summary

This project contains an Ansible role that installs the [Amazon CloudWatch agent](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Install-CloudWatch-Agent.html) 
onto an Ubuntu server. This has been created specifically for use in the process of building golden AMIs for EC2 
instances. It is built to operate in a context-free environment where the details of the eventual application that will 
run on the server is unknown.

## Key features

- Installs the Amazon CloudWatch Agent.
- Enables a default log configuration, where `/var/log/syslog` will be written to a stream in the 
  `/aws/ec2/{instance_id}` log group.
- Sets up sensible defaults for rotating the Amazon CloudWatch Agent log files.

## Usage

This role is not currently published to the Ansible Galaxy registry. As such, it should be included in the Ansible 
`requirements.yml` file in the format shown below.

```yaml
# requirements.yml

- src: https://github.com/entanet-devops/cloudwatch-agent-golden
  version: {branch_name}
  name: entanet_devops.amazon_cloudwatch_agent_golden
```

## Testing

You can verify that the CloudWatch agent has been installed and configured successfully on the server by running:

```sh
amazon-cloudwatch-agent-ctl -a status
```

## License

This is heavily based upon the [entanet-devops/cloudwatch-agent](https://github.com/entanet-devops/cloudwatch-agent)
repository, which is forked from the original [christiangda/ansible-role-amazon-cloudwatch-agent](https://github.com/christiangda/ansible-role-amazon-cloudwatch-agent) 
repository. As per the terms of the original license, this project retains the GPLv3 license. 