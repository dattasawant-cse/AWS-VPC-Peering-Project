# AWS VPC Peering - Connectivity Testing

## 1. Objective

Verify private connectivity between App-A and App-B after configuring VPC peering, route tables and security groups.

## 2. Identify the Instances

Run these commands inside each EC2 instance:

```bash
hostname
hostname -I
```

## 3. Baseline Test

Before establishing peering and adding peer routes, run on App-A:

```bash
ping -c 4 10.20.1.10
```

Expected result: No replies before peering routes are configured.

Record the actual output.

## 4. Forward Connectivity Test

After peering becomes active and routes are configured, run on App-A:

```bash
ping -c 4 10.20.1.10
```

Expected result: Four replies, with zero packet loss, if all routes and security rules are correct.

## 5. Reverse Connectivity Test

Run on App-B:

```bash
ping -c 4 10.10.2.10
```

Expected result: Four replies, with zero packet loss, if all routes and security rules are correct.

## 6. SSH Test

From the student's laptop, connect to App-B through the bastion using SSH ProxyJump.

```bash
ssh ewb-app-b
```

This command requires the local SSH configuration and key described in the project setup guide.

## 7. Controlled Failure and Recovery

1. Temporarily remove only the App-B inbound ICMP Echo Request rule for App-A.
2. Repeat the ping test from App-A.
3. Confirm that replies stop.
4. Restore the exact rule.
5. Repeat the ping test and confirm connectivity returns.

Keep the SSH rule in place during this test.

## 8. Evidence

Save screenshots showing:
- Baseline ping failure.
- Successful ping from App-A to App-B.
- Successful ping from App-B to App-A.
- SSH access to App-B through the bastion.
- Controlled failure and recovery.

## 9. Test Results

Actual results will be recorded after the AWS deployment. Expected results are not proof of a completed test.
