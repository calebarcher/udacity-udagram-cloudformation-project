# udacity-udagram-cloudformation-project
in this project, I have written cloudformation scripts using YAML that will create AWS resources. The deployed cloudformation stack will create a VPC that will have resources deployed accross 2 AZs. 
Each availability zone will contain a private and public subnet. The private subnets hold our webservers which are managed by an auto-scaling group config. The webservers only allow incoming traffic on port 80. The public subnets hold our NATs that enable our webservers in the private subnet to reach the internet.
A load balancer is used to manage the traffic load to our resources.

I have included a Bastion host/Jump box in one of the public subnets to allow me SSH into the webservers in the private subnets using their private IP addresser

The cloudormation scripts are seperated into 2 files as follows:
1. **udagram-network.yml:** This file contains the scripts for creating our VPC, subnets and routing rules and resources. This file also contains an outputs section. its parameter file is "udagram-network-params.json"
2. **udagram-servers.yml:** This file contains the scripts for creating our EC2 instances, security groups auto-scaling and load balancer. It outputs the DNS name of our load banalcer. its parameter file is "udagram-servers-params.json"

**LOAD-BALANCER DNS URL**
http://udagr-webap-wcme27ewiabd-41043254.us-east-1.elb.amazonaws.com/
