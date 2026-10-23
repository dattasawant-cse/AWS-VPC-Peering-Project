# AWS VPC Peering Project

## Project Overview
This project demonstrates private network connectivity between two Amazon Virtual Private Clouds (VPCs) using AWS VPC Peering.

## Objectives
- Create two separate VPCs.
- Configure public and private subnets.
- Establish a VPC Peering connection.
- Configure route tables and security groups.
- Verify private connectivity between EC2 instances.

## AWS Architecture

### VPC A
- CIDR: `10.10.0.0/16`
- Public subnet: `10.10.1.0/24`
- Private subnet: `10.10.2.0/24`
- Bastion Host: `10.10.1.100`
- App-A: `10.10.2.48`

### VPC B
- CIDR: `10.20.0.0/16`
- Private subnet: `10.20.1.0/24`
- App-B: `10.20.1.36`

## AWS Services Used
- Amazon VPC
- Amazon EC2
- VPC Peering
- Route Tables
- Internet Gateway
- Security Groups

## Connectivity Testing

The VPC Peering connection was active during testing.

| Test | Result |
|---|---|
| Bastion to App-A ping | Successful |
| Bastion to App-B ping | Successful |
| App-A to App-B ping | Successful |
| App-B to App-A ping | Successful |
| SSH from Bastion to private instances | Successful |

Both application instances communicated using private IP addresses, and the ping tests completed with 0% packet loss.

Detailed results are available in [testing.md](testing.md).

## Project Documentation
- [Architecture](architecture.md)
- [Route Tables](route-tables.md)
- [Security Groups](security-groups.md)
- [Connectivity Testing](testing.md)

- 
## Project Screenshots

### App-A to App-B Connectivity
![App-A to App-B Ping Test](app-a-to-app-b-ping.png)

### App-B to App-A Connectivity
![App-B to App-A Ping Test](app-b-to-app-a-ping.png)

## Conclusion
The project successfully demonstrates private communication between two AWS VPCs through VPC Peering, with routing and security group rules configured to allow the required traffic.
