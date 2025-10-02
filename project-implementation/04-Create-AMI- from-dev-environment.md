#04 — Create AMI from Dev Environment

## Goal
Capture the development EC2 instance as an Amazon Machine Image (AMI) for reuse in other Regions.

## Steps
1. Set hostname and create SSH key:
```bash
sudo hostname cafeserver
ssh-keygen -t rsa -f ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
```
2. Create **CafeServer** AMI from **CafeWebServer** EC2 instance.
3. Wait and verify until state is **Available**

## Notes
- An AMI is a snapshot of the configured instance.
- Generally used for scaling, migrations, or disaster recovery. 

## Screenshot
![Step 04](04-create-AMI-from-dev-environment.png)




