
# SETTING UP SCALING GROUPS

<h2>Create an Amazon Machine Image (AMI)</h2>
b. Configure the Instance
SSH into the EC2 instance and install the necessary software and applications.
After configuring the instance, return to the EC2 Dashboard.

<h2>create launch template</h2>
- In the EC2 Dashboard, navigate to Launch Templates.
- Click Create launch template.
Provide a name and description for the template.
Under Launch template contents, configure the following:
AMI ID: Select the AMI created in the previous step.
Instance Type: Choose the instance type.
Key Pair: Select an existing key pair or create a new one.
Security Groups: Select the appropriate security groups.
Configure other settings as needed (e.g., network interfaces, storage).
Click Create launch template
<br />

<h2>Features</h2>

- <b>VPC with 2 public subnets and 4 private subnets</b> 
- <b>Internet gateway for internet access</b>
- <b>NAT Gateway for outbound internet access for instances in Private Subnets </b> 
- <b>EC2 instances for the two applications and bastion host</b>
- <b>RDS instance (database)</b> 
- <b>2 load balancers to handle the traffic</b>
- <b>Auto scaling groups</b> 
- <b>Security groups (firewalls)</b>

<h2>Interactions in the VPC</h2>
The overall solution architecture is made of a VPC that is connected to the internet. The VPC serves as the foundation of the network from which AWS resources can be lunched. For the internet to reach the resources inside of the VPC, an Internet Gateway (IGW in the template) must be created. An IGW acts as a channel for communication between resources in the VPC and the internet. Note that the IGW is connected to the VPC via the VPCtoIGWConnection (VPCGatewayAttachment). In the VPC, there are public subnets and private subnets that will contain the resources that will be used for the project including EC2 instances. Public Private subnet 1 host to web application instances that manage user interactions and receives communication over the internet using port 80. These instances connect to the internet via an Internet Gateway (IGW), which allows both incoming and outgoing traffic. The Application Load Balancer (ALB) distributes incoming traffic evenly among the web instances, ensuring that no one instance is overloaded and therefore improving scalability and flexibility. In Private subnets 1 and 2 there are also API Endpoint instances. Those instances allow programmatic access to the application over port 5000, which is only accessible by web instances via configured security groups. The private subnets connect to the internet via NAT Gateways which prevents direct internet access of the private subnets from the internet. The database instance (RDS) is on private subnet 3 and 4 and cannot be accessed directly from the internet. It is only accessible from the web application instance with read and write access enabled using IAM roles. The RDS Database instance can also be accessible It enables high availability with multi-AZ deployment, ensuring uninterrupted operation during disruptions. Security groups and IAM roles maintain access controls, enabling only authorized instances to interface with the database and therefore assuring more security within the VPC..
<br />

<h2>Steps to execute the project</h2>

- <b>Launch the cloud formation template attached</b> 
- <b>Create a bastion host</b>
- <b>Create a launch template and configure scaling groups</b> 
- <b>Create application load balancers</b>
- <b>Update scaling groups</b>



# Create an Amazon Machine Image (AMI)
a. Launch an EC2 Instance
Open the AWS Management Console.
Navigate to the EC2 Dashboard.
Click Launch Instance.
Choose an Amazon Machine Image (AMI).
Select an Instance Type.
Configure Instance Details, add Storage, and configure Security Groups as per your requirements.
Review and Launch the instance.
b. Configure the Instance
SSH into the EC2 instance and install the necessary software and applications.
After configuring the instance, return to the EC2 Dashboard.
c. Create an AMI
Select the configured instance.
Click Actions > Image > Create Image.
Provide an image name and description.
Click Create Image.
2. Create a Launch Template
In the EC2 Dashboard, navigate to Launch Templates.
Click Create launch template.
Provide a name and description for the template.
Under Launch template contents, configure the following:
AMI ID: Select the AMI created in the previous step.
Instance Type: Choose the instance type.
Key Pair: Select an existing key pair or create a new one.
Security Groups: Select the appropriate security groups.
Configure other settings as needed (e.g., network interfaces, storage).
Click Create launch template.
3. Set Up an Auto Scaling Group
a. Navigate to the Auto Scaling Groups Section
In the AWS Management Console, go to the EC2 Dashboard.
Under Auto Scaling, click Auto Scaling Groups.
b. Create an Auto Scaling Group
Click Create Auto Scaling group.
Provide a name for the Auto Scaling group.
Select the launch template created in the previous step.
Click Next.
c. Configure the Group Size and Scaling Policies
Specify the Group size (desired, minimum, and maximum number of instances).
Configure the Network and Subnets.
Click Next.
d. Configure Scaling Policies
Choose scaling policies based on your needs:
Target Tracking Scaling: Adjusts the number of instances based on a target value for a specific metric (e.g., CPU utilization).
Step Scaling: Adjusts the number of instances in steps based on metric thresholds.
Scheduled Scaling: Adjusts the number of instances based on a schedule.
Configure the chosen scaling policy.
Click Next.
e. Add Notifications (Optional)
Configure notifications to receive alerts on scaling events.
Click Next.
f. Add Tags (Optional)
Add tags to organize and manage resources.
Click Next.
g. Review and Create the Auto Scaling Group
Review the configuration details.
Click Create Auto Scaling group.
