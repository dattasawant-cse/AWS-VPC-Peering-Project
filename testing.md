# AWS VPC Peering - Connectivity Testing

## 1. Objective

To verify private network connectivity between App-A and App-B after configuring AWS VPC Peering, route tables, and security groups.

## 2. AWS Environment

- **Region:** Asia Pacific (Sydney) - `ap-southeast-2`
- **VPC A CIDR:** `10.10.0.0/16`
- **VPC B CIDR:** `10.20.0.0/16`
- **VPC Peering:** Active

## 3. EC2 Instances

| Instance | Private IP | Role |
|---|---|---|
| Bastion | `10.10.1.100` | Secure access to private instances |
| App-A | `10.10.2.48` | Application instance in VPC A |
| App-B | `10.20.1.36` | Application instance in VPC B |

## 4. Connectivity Test Results

### Test 1: Bastion to App-A

Command:

`ping -c 4 10.10.2.48`

Result: **SUCCESS** — 4 packets received, 0% packet loss.

### Test 2: Bastion to App-B

Command:

`ping -c 4 10.20.1.36`

Result: **SUCCESS** — 4 packets received, 0% packet loss after configuring the required ICMP security group rule.

### Test 3: App-A to App-B

Command:

`ping -c 4 10.20.1.36`

Result: **SUCCESS** — 4 packets received, 0% packet loss.

### Test 4: App-B to App-A

Command:

`ping -c 4 10.10.2.48`

Result: **SUCCESS** — 4 packets received, 0% packet loss.

### Test 5: SSH Access to Private Instances

SSH access from the Bastion host to App-A and App-B was successfully verified using the EC2 key pair.

Result: **SUCCESS**

## 5. Conclusion

VPC Peering connectivity between VPC A and VPC B was verified successfully. The route tables and security group rules allowed private communication between App-A and App-B in both directions without requiring a public IP address on either application instance.
