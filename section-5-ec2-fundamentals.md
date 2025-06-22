# Week 2: EC2 Fundamentals & Instance Access

## EC2 Basics
- EC2 = Elastic Compute Cloud → virtual servers in the cloud.
- You choose:
  - AMI (Amazon Machine Image) → OS + preinstalled software.
  - Instance type → determines CPU, memory, networking.
  - Key pair → used for SSH authentication.
  - Security group → acts as a virtual firewall.

## Security Groups
- Security groups = **stateful** firewalls.
- They control **inbound and outbound** traffic.
- Only allow the **ports and protocols you need** (e.g., port 22 for SSH, 80 for HTTP).
- You must **explicitly open ports** — everything is denied by default.
- Modifying a security group applies immediately to all associated instances.

## SSH Access
- SSH = Secure Shell (used to connect to EC2 Linux instances).
- You connect using your private key:
  ```bash
  ssh -i my-key.pem ec2-user@<public-ip>
  ```
- Key rules:
  - `.pem` file must have `chmod 400` permissions.
  - Use correct default usernames (e.g., `ec2-user`, `ubuntu`, `admin`, `centos`).

## EC2 Instance Connect
- Browser-based way to connect to EC2.
- No need to manage SSH keys (as long as the instance has a public IP and EC2 Connect is enabled).

## User Data
- Shell script run **once at instance launch**.
- Used for bootstrapping (e.g., installing packages, starting services).
- Example: Set up a web server on launch:
  \`\`\`bash
  #!/bin/bash
  yum update -y
  yum install -y httpd
  systemctl start httpd
  systemctl enable httpd
  \`\`\`

## Instance Types
- Named by family + size (e.g., `t3.micro`, `m5.large`).
- Families:
  - `t` = general purpose
  - `m` = balanced
  - `c` = compute-optimized
  - `r` = memory-optimized
- Use small instances (`t2.micro`) for testing and free tier.

## EC2 Pricing & Budgets
- Instance cost = time running (on-demand, spot, reserved).
- You are charged **for elastic IPs** if they’re not associated with a running instance.
- Budgets can be created in the Billing section to track usage and prevent surprises.
