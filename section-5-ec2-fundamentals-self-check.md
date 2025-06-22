# Week 2 Self-Check: EC2 Fundamentals

Check off what you can confidently answer or demonstrate:

- [x] What are the key components to launch an EC2 instance?
  - Amazon Machine Image (AMI):
    - Defines the operating system and base configuration (e.g., Amazon Linux, Ubuntu, Windows). 
    - May also include preinstalled software.
  - Instance type:
    - Determines the hardware of the host (CPU, memory, network performance).
    - Examples: t2.micro (free tier), m5.large, c6g.medium.
  - Key Pair (for SSH):
    - Used to securely connect to the instance via SSH (Linux) or RDP (Windows).
    - You download the .pem file once — store it safely.
  - Security Group:
    - Acts as a virtual firewall that controls inbound/outbound traffic.
    - You must explicitly allow required ports (e.g., 22 for SSH, 80 for HTTP).
  - Network Configuration:
    - Select the VPC, subnet, and optionally a public IP address.
    - Needed to control accessibility and placement of the instance.
  - Storage (EBS Volume):
    - Define the root volume size/type (SSD, magnetic).
    - Optionally attach additional volumes.
  - User Data Script (optional):
    - A shell script that runs at launch time.
    - Used for bootstrapping, such as installing software or configuring services.
- [x] What does a security group do, and how is it different from a traditional firewall?
  - A security group acts as a virtual firewall that controls inbound and outbound traffic to AWS resources like EC2 instances.
  - A security group has only "Allow" rules, is stateful, and can reference other security groups as trusted sources
- [x] How does EC2 SSH access work, and how do you troubleshoot connection issues?
  - AWS EC2 uses public-key cryptography for secure remote access to Linux instances.
  - When you launch an EC2 instance, you select a key pair:
    - The public key is automatically placed in the instance (typically in ~/.ssh/authorized_keys).
    - The private key (a .pem file) is downloaded and stored by you.
  - You connect like this:
    - ssh -i /path/to/key.pem ec2-user@<EC2-Public-IP>
  - AWS does not store your private key, and you cannot retrieve it again if lost.
  - Troubleshooting:
    - Correct Username
    - Correct Key Permissions
    - Correct Key and Public Key Pairing
    - Correct Public IP Address
    - Security Group Rules
    - Running EC2 Instance
    - Network ACLs and VPC Configuration
    - Firewall on the Instance
    - Instance Reachability
- [x] How can you connect to an EC2 instance without using a key pair?
  - EC2 Instance Connect (browser-based SSH)
- [x] What is EC2 Instance Connect, and when would you use it?
  - It is a browser-based SSH available in AWS Console.
  - Use cases:
    - Quick, one-time access to troubleshoot or inspect an EC2 instance.
    - Lost your .pem file and can't SSH the traditional way.
    - You want to avoid managing local SSH key files.
    - You're in a training/lab environment or demo scenario.
- [x] What is EC2 user data, and when does it run?
  - It is a script (usually a shell script) that you can attach to an instance at launch time. It is executed automatically when the instance boots for the first time.
- [x] Can you write a simple user data script to install a web server?
  - #!/bin/bash
    yum update -y
    yum install -y httpd
    systemctl start httpd
    systemctl enable httpd
- [x] What are the different EC2 instance families and their purposes?
  - t = burstable, cheap (general purpose)
  - m = balanced (general purpose)
  - c = compute-heavy workloads
  - r = RAM-heavy workloads
  - i,d,h = disk-heavy workloads (IOPS, throughput)
  - g = GPU for ML or rendering
- [x] What happens when you allocate an Elastic IP but don’t use it?
  - You’re charged if you reserve an Elastic IP and don’t use it. AWS wants you to associate it with a running instance, or release it.
- [x] What are the main EC2 pricing models? Which is best for testing?
  - On-demand = Pay by the second (or hour), no commitment.
  - Reserved = 1 or 3-year commitment for a specific instance type — big discount (up to 75%)
  - Spot = Use unused EC2 capacity at steep discounts (up to 90%) — but can be terminated anytime
  - Dedicated Host = Physical server dedicated to your use (for compliance/licensing needs)
  - Savings Plans = Flexible commitment (1/3 years) for overall compute usage, not instance-specific
  - Best for testing = On-demand -> No upfront commitment, Instances can be launched and terminated at will, Billing is per-second (for Linux)
