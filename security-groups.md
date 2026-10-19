# AWS VPC Peering - Security Groups

## 1. Overview

Security groups control inbound and outbound traffic for EC2 instances.

## 2. Bastion Security Group - ewb-sg-bastion

| Type | Protocol / Port | Source |
|---|---|---|
| SSH | TCP 22 | Student's current public IPv4 address /32 |

Purpose: Allows SSH access to the bastion from the student's current public IP.

## 3. App-A Security Group - ewb-sg-app-a

| Type | Protocol / Port | Source |
|---|---|---|
| SSH | TCP 22 | 10.10.1.10/32 |
| ICMP Echo Request | ICMPv4 | 10.20.1.10/32 |

Purpose: Allows SSH from the bastion and ping requests from App-B.

## 4. App-B Security Group - ewb-sg-app-b

| Type | Protocol / Port | Source |
|---|---|---|
| SSH | TCP 22 | 10.10.1.10/32 |
| ICMP Echo Request | ICMPv4 | 10.10.2.10/32 |

Purpose: Allows SSH from the bastion and ping requests from App-A.

## 5. Security Notes

- Do not expose SSH to 0.0.0.0/0.
- Use the actual bastion public IP source for SSH access to the bastion.
- Keep App-A and App-B without public IPv4 addresses.
- Security groups are stateful, so response traffic for allowed connections is permitted automatically.
- Keep the default outbound rules for this lab unless the instructor specifies otherwise.

## 6. Deployment Status

These are the planned security rules. Verify them in the AWS console after deployment.
