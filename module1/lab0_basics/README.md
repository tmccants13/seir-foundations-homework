# SEIR Foundations — Module 1, Lab 0 Homework

## Three EC2 Deployments

For this assignment, I deployed three separate Amazon Linux 2023 EC2 instances using my saved AWS launch template, `SEIR-Lab0-Template`.

I used the `t3.micro` instance type in the `us-east-1` region and connected through EC2 Instance Connect.

## Deployment Evidence

| Deployment | Public IPv4 Address | Connection Method | Screenshot | Instance Terminated? |
|---|---|---|---|---|
| 1 | 3.235.135.182 | EC2 Instance Connect | [deployment-1.png](screenshots/deployment-1.png) | Yes |
| 2 | TO BE ADDED | EC2 Instance Connect | [deployment-2.png](screenshots/deployment-2.png) | Yes |
| 3 | TO BE ADDED | EC2 Instance Connect | [deployment-3.png](screenshots/deployment-3.png) | Yes |

## Deployment 1

I launched an Amazon Linux 2023 EC2 instance from my saved launch template. After the instance started and passed its status checks, I connected through the browser-based EC2 Instance Connect service. The SEIR dashboard displayed system information including CPU usage, memory, disk usage, and uptime. I captured a screenshot and terminated the instance after completing the deployment.

## Deployment 2

I repeated the deployment process using the same launch template. I connected to the new instance through EC2 Instance Connect, verified the SEIR dashboard, saved a screenshot, and terminated the instance.

## Deployment 3

I launched a third EC2 instance using the saved template. I connected through EC2 Instance Connect, checked the SEIR dashboard, captured the third screenshot, and terminated the instance.

## Understanding the Dashboard

- **CPU:** Shows how much processing capacity the server is using.
- **Memory:** Shows how much RAM is currently being used and how much is available.
- **Disk:** Shows how much storage space is used and how much remains.
- **Uptime:** Shows how long the server has been running since it started.

## What Became Easier

Repeating the deployment process helped me become more familiar with launching EC2 instances from a template, finding their public IPv4 addresses, and connecting to Linux servers through EC2 Instance Connect.

## Errors and Troubleshooting

During the lab, I reviewed the security group settings and configured outbound access and SSH connectivity to allow the instance to connect successfully.

## Cleanup

I terminated the three homework EC2 instances after collecting the required evidence. I retained my launch template, `SEIR-Lab0-Template`, for future labs.
