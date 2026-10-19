# AWS VPC Peering - Route Tables

## 1. Overview

Route tables determine where network traffic is directed. This project uses three custom route tables for VPC A and VPC B.

## 2. Public Route Table - ewb-rt-a-public

Associated subnet: `ewb-a-public`

| Destination | Target | Purpose |
|---|---|---|
| 10.10.0.0/16 | local | Communication within VPC A |
| 0.0.0.0/0 | Internet Gateway | Bastion internet connectivity |
| 10.20.0.0/16 | VPC Peering Connection | Access to VPC B through peering |

## 3. Private Route Table - ewb-rt-a-private

Associated subnet: `ewb-a-private`

| Destination | Target | Purpose |
|---|---|---|
| 10.10.0.0/16 | local | Communication within VPC A |
| 10.20.0.0/16 | VPC Peering Connection | App-A to VPC B |

## 4. Private Route Table - ewb-rt-b-private

Associated subnet: `ewb-b-private`

| Destination | Target | Purpose |
|---|---|---|
| 10.20.0.0/16 | local | Communication within VPC B |
| 10.10.0.0/16 | VPC Peering Connection | Return path to VPC A |

## 5. Configuration Notes

- Keep the existing local routes.
- Replace the VPC Peering Connection target with the actual peering connection ID.
- Associate each route table with the correct subnet.
- The peering connection must be active.
- Both VPCs need routes for communication in both directions.

## 6. Deployment Status

These are the planned route table entries. Verify and update them in the AWS console after deployment.
