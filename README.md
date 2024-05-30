# VPC-AWS
Highly available, secure and scalable VPC architecture in AWS 

<h2>General Information</h2>
Amazon Web Services (AWS) is a subsidiary of Amazon that provides on-demand cloud computing platforms and APIs to individuals, companies, and governments, on a metered, pay-as-you-go basis. 
AWS is the world’s most comprehensive and broadly adopted cloud, offering over 200 fully featured services from data centers globally. <br/>
AWS offers the widest variety of databases that are purpose-built for different types of applications so you can choose the right tool for the job to get the best cost and performance. AWS is architected to be the most flexible and secure cloud computing environment available today. 
With AWS, you can leverage the latest technologies to experiment and innovate more quickly. 
AWS provides a highly reliable, scalable, low-cost infrastructure platform in the cloud that powers hundreds of thousands of businesses in 190 countries around the world.

The official home of AWS is https://aws.amazon.com.

<h2> Project Description</h2>
This project aims to create an AWS infrastructure using CloudFormation templates. The setup includes a Virtual Private Cloud (VPC) with multiple public and private subnets, internet gateways, NAT gateways, security groups, EC2 instances, and an RDS database. The infrastructure supports two main applications: a Café web application and an API application, each with its own security configurations and resource allocations. This project is designed for deploying web and API applications with secure, scalable, and highly available infrastructure components. By incorporating load balancers, auto scaling groups, NAT gateways, carefully configured security groups, and a high-availability RDS instance, the project shows how to set applications using AWS that are both secure and capable of handling varying loads efficiently.
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

<h2>Configurations</h2>




