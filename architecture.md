# AWS VPC Peering Architecture

## 1. Architecture Overview

This project connects two Amazon VPCs using a VPC Peering connection. The application servers use private IPv4 addresses to communicate.

## 2. Network Diagram

```text
                   Student Laptop
                         |
                      SSH (22)
                         |
                  Internet Gateway
                         |
             VPC A: 10.10.0.0/16
                         |
               Public Subnet A
                 10.10.1.0/24
                         |
                    Bastion EC2
                   10.10.1.10
                         |
             Private Subnet A
                 10.10.2.0/24
                         |
                    App-A EC2
                   10.10.2.10
                         |
                  VPC Peering
                         |
             Private Subnet B
                 10.20.1.0/24
                         |
                    App-B EC2
                   10.20.1.10
                         |
             VPC B: 10.20.0.0/16
```

## 3. IP Address Plan

| Resource | CIDR / Private IP |
|---|---|
| VPC A | 10.10.0.0/16 |
| Public Subnet A | 10.10.1.0/24 |
| Private Subnet A | 10.10.2.0/24 |
| Bastion EC2 | 10.10.1.10 |
| App-A EC2 | 10.10.2.10 |
| VPC B | 10.20.0.0/16 |
| Private Subnet B | 10.20.1.0/24 |
| App-B EC2 | 10.20.1.10 |

## 4. Traffic Flow

1. The student connects to the bastion host using SSH.
2. The bastion provides SSH access to the private application instances.
3. App-A communicates with App-B using the VPC Peering connection.
4. Route tables provide forward and return paths.
5. Security groups restrict inbound traffic to the required sources.

## 5. Security Design

- App-A and App-B do not require public IPv4 addresses.
- VPC B has no internet gateway.
- SSH access is restricted to the required sources.
- ICMP Echo Request is permitted between the application hosts for connectivity testing.

## 6. Deployment Status

This document describes the planned architecture. Actual AWS resource IDs and connectivity test results will be recorded after deployment.
