# TP1 - AWS

## VPC (Virtual Private Cloud)
Virtual Network that looks like your own datacenter

### Scenario
- Public subnet: Can receive traffic from the Internet
- Private subnet: Can only receive traffic from the subnet

- CIDR (Classless Inter-Domain Routing): method of assigning Internet Protocol

## Subnet
Subnet is a part of a VPC

## Internet Gateway
Allows traffic from the Internet to be routed to the VPC

## Route table
Route table is a collection of routes that are used to define the network routing policy
- In the TP we will use the default route table to expose a public subnet

## IP Forwarding on EC2 instance
```sh
#!/bin/bash 
sysctl -w net.ipv4.ip_forward=1 
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
```

## Questions 
### How to control and limit the access to an instance?
To control and limit the access, there's a couple of options:
    - IAM (Identity and Access Management): In case you want to prevent access to an instance internally, you can use IAM to control the access.
    - Internet Gateway & NAT: In case you want to limit the access to an instance from outside, you can use an Internet Gateway & NAT to control the access.
### What does private network instances need to communicate with the internet to fetch packages and updates?
They need to use a NAT gateway to connect to the internet.
### What are the properties that describe a "Public Subnet" in AWS?
- It is a subnet that is accessible from the Internet
- It is a subnet that can send traffic to the Internet
### Security Groups are stateless or stateful?
Security groups are stateful. For example, if you send a request from an instance, the response traffic for that request is allowed to reach the instance regardless of the inbound security group rules. Responses to allowed inbound traffic are allowed to leave the instance, regardless of the outbound rules
### What the "Default" route table is used for?
The default route table is used to define the network routing policy.
### How to connect to an instance located in a private subnet?
Connect to an instance located in a public subnet that is connected to the private network by a NAT gateway, then ssh your way to the private one.