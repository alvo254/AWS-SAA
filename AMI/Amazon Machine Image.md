This is a template to configure new instances
You can turn you EC2 instances into AMIs so you cab create copies of your servers
An AMI has the following information:
- A template for the root volume for the instance(EBS snapshot or instance store template) eg an OS, an application server and applications
- Launch permissions that can control which AWS acc can use that AMI to launch instances.
- A block device mapping that specifies the volumes to attach the instance when its launched.