# AWS VPC Peering Project

## Project Overview
This project demonstrates private communication between two Amazon Virtual Private Clouds (VPCs) using AWS VPC Peering.

## Objectives
- Create two VPCs with non-overlapping CIDR blocks.
- Configure public and private subnets.
- Launch EC2 instances.
- Establish a VPC peering connection.
- Configure route tables and security groups.
- Test private connectivity using ping and SSH.

## Network Design

### VPC A
- CIDR: `10.10.0.0/16`
- Public subnet: `10.10.1.0/24`
- Private subnet: `10.10.2.0/24`
- Bastion host: `10.10.1.10`
- App-A: `10.10.2.10`

### VPC B
- CIDR: `10.20.0.0/16`
- Private subnet: `10.20.1.0/24`
- App-B: `10.20.1.10`

## Technologies
- Amazon Web Services (AWS)
- Amazon VPC
- Amazon EC2
- VPC Peering
- Route Tables
- Security Groups
- SSH and ICMP

## Expected Outcome
The two private application instances should communicate through the active VPC peering connection after the correct routes and security rules are configured.

## Project Status
Documentation created. AWS deployment and connectivity tests are pending.

## Author
Student Project
