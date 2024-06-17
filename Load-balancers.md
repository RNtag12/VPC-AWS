
# SETTING UP 2 LOAD BALANCERS

Creating 2 load balancers (for web app and API enpoint) that will be used to distribute the traffic. 
I created a load balancer for the web app that listens to port 80 and another load balancer that listens to port 5000 for the API endpoints

## Specifications for the load balancers
<b>Key Specifications include:</b>
- Name (choose any)
- Scheme and IP address type do not need to be changed
- Specify Rod_VPC and include relevant subnets (public subnets)
- Select cafeSG as security group
- Create a target grpup and choose instances as target type
- In the network settings, select Rod_VPC and select Public subnet 1 and Public subnet 2
- For the security groups, for web server select the cafeSG as the security group and select APISG
- Listeners and routing details
  - http:80 (for Web app), http:5000 (for API endpoint)
  - select create a target group for each of them (web app and API endpoint)
  - select them then finally click create the load balancer


-
