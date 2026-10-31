# AWS VPC Peering – Private Connectivity Between Two VPCs

## Project Overview

This project demonstrates how to establish private network connectivity between two Amazon Virtual Private Clouds (VPCs) using AWS VPC Peering.

The architecture uses two isolated VPCs with non-overlapping CIDR blocks, private EC2 instances, custom route tables, security groups and a bastion host for secure SSH administration.

The project was completed as part of the EWB Cloud Labs AWS Internship – Project 01.

## Architecture

| Component | Configuration |
|---|---|
| Cloud Provider | AWS |
| AWS Region | Asia Pacific (Mumbai) – ap-south-1 |
| VPC A | 10.10.0.0/16 |
| VPC B | 10.20.0.0/16 |
| Public Subnet | 10.10.1.0/24 |
| Private Subnet A | 10.10.2.0/24 |
| Private Subnet B | 10.20.1.0/24 |
| Compute | 3 EC2 instances |
| Operating System | Amazon Linux 2023 |
| Connectivity | VPC Peering |
| Administration | Bastion Host with SSH ProxyJump |

## AWS Services and Concepts Used

- Amazon VPC
- VPC Peering Connections
- Amazon EC2
- Internet Gateway
- Public and Private Subnets
- Custom Route Tables
- Security Groups
- CIDR Addressing
- SSH and ProxyJump
- ICMP Connectivity Testing

## Implementation

1. Created two VPCs with non-overlapping CIDR ranges.
2. Created public and private subnets with explicit route table associations.
3. Configured an Internet Gateway for VPC A.
4. Launched three EC2 instances: one bastion host and two private application instances.
5. Configured security groups to allow restricted SSH and ICMP traffic.
6. Established and accepted the VPC peering connection.
7. Added forward and return routes to the respective route tables.
8. Configured SSH ProxyJump to access private instances through the bastion host.

## Testing and Validation

| Test | Result |
|---|---|
| Connectivity before peering | Failed as expected |
| App-A to App-B private connectivity | Successful |
| App-B to App-A private connectivity | Successful |
| SSH access to App-B through bastion | Successful |
| Private instance public IP isolation | Verified |
| Controlled security group failure | Demonstrated |

## Troubleshooting

During implementation, I encountered and resolved:

- Bastion instance launching without a public IPv4 address.
- SSH configuration file saved with an incorrect extension.
- Incorrect ICMP Echo Reply rule instead of Echo Request.
- Connectivity failures caused by missing or incorrect security group rules.

These issues helped me understand how routing and security groups independently affect network connectivity.

## Key Learnings

- How VPC peering establishes private connectivity between VPCs.
- Why both forward and return routes are necessary.
- How security groups control traffic between peered VPCs.
- How to securely access private EC2 instances using a bastion host.
- How to troubleshoot network connectivity layer by layer.

## Project Documentation

Detailed implementation steps, AWS configurations, terminal outputs, screenshots and troubleshooting evidence are available in the `docs/` directory.

## Project Source

EWB Cloud Labs – AWS Internship Batch 1.1  
Project 01: AWS VPC Peering

**Author:** Shubham Kalekar
