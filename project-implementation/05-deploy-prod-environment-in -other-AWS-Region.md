# 05 — Deploy Production Environment in Another AWS Region

## Goal
Launch a production version of the café application in us-west-2, based on the AMI created in us-east-1.

## Steps
1. Copy `CafeServer` AMI to **Oregon (us-west-2)**.
2. Switch AWS Region to **Oregon (us-west-2)**.
2. Launch new instance `ProdCafeServer` from AMI `CafeServer`
3. Get public DNS of instance.
4. Update setup script with Region + DNS:
```bash
cd ~/environment/setup/
nano set-app-parameters.sh
# region="us-west-2"
# publicDNS="ec2-54-202-178-85.us-west-2.compute.amazonaws.com"
```
5. Run parameters script again:
```bash
./set-app-parameters.sh
```
6. Verify in browser:
   - http://ec2-54-202-178-85.us-west-2.compute.amazonaws.com/cafe
   - Place order → check Order History.

## Notes
   - Separation of Dev (us-east-1) and Prod (us-west-2) ensures safer deployments.
   - Multi-Region design adds resilience and disaster recovery capability.

## Screenshot
![Step 05](05-deploy-prod-environment-in-other-AWS-Region-1.png)
![Step 05](05-deploy-prod-environment-in-other-AWS-Region-2.png)

