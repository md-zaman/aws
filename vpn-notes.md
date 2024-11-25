# AWS Certified Advanced Networking - Specialty 2024 
## By Zeal Vora
### Section 6: Virtual Private Networks IPSec Tunnels and Transit Gateways

#### Bastion Hosts & SSH Agent Forwarding

1. Bastion hosts are also referred to as jump box acts like proxy server and allows the client machines to connect to the remote server in the private subnets.

   Client ----> Bastion (Public Subnet) ----> EC2 Instances (Private Subnet)

2. Challenge with this Setup
   - Every user have private keys stored securely on their laptop.
   - This private key can be used to connect to Bastion Host.
   - Once logged into Bastion, how will he login to pvt EC2 instance.

     [keys] Clients ----> Bastion (Public Subnet) ----> Private EC2

3. SSH Agent Forwarding
   SSH Agent forwarding allows users to use theit local SSH keys to perform some operatio on remote servers without keys being left from your workstation.



   



