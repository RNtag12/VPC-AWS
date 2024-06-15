
# SETTING UP AUTO SCALING GROUPS

<h2>Create launch template</h2>

- In the EC2 Dashboard, navigate to Launch Templates.
- Click Create launch template and provide a name and description for the template.
- Under Launch template contents, configure the following:
    - AMI ID: choose an AMI (here an Amazon Linux 2023 AMI is used).
    - Instance Type: Choose the instance type t2.micro.
    - Key Pair: Select an existing key pair or create a new one.
    - Select a subnet (either private subnet1 for APP instances or private subnet2 for API instances)
    - Security Groups: Select the appropriate security groups
      - for API ec2 instances select APISG.
      - for APP ec2 instances select CafeSG.
    - Configure other settings as needed (e.g., network interfaces, storage).
- Click Create launch template
<br />

## Setting Up an Auto Scaling Group

- Navigate to the Auto Scaling Groups Section In the AWS Management Console, go to the EC2 Dashboard.
Under Auto Scaling, click Auto Scaling Groups.
- Create Auto Scaling group.
  - Provide a name for the Auto Scaling group.
  - Select the launch template created in the previous step. Click Next.
- Configure the Group Size and Scaling Policies
  - Specify the Group size (desired, minimum, and maximum number of instances).
  - Configure the Network and Subnets. Click Next.
- Configure Scaling Policies
  - Choose scaling policies based on your needs:
  - Target Tracking Scaling: Adjusts the number of instances based on a target value for a specific metric (e.g., CPU utilization).
  - Step Scaling: Adjusts the number of instances in steps based on metric thresholds.Scheduled Scaling: Adjusts the number of instances based on a schedule.
  - Configure the chosen scaling policy. Click Next.
- Review and Create the Auto Scaling Group
  - Review the configuration details.
  - Click Create Auto Scaling group.
