# Terraform script for provisioning boxes on Hetzner cloud
Get an API-Key on Hetzner cloud. Use it to access the Hetzner API with terraform.
```bash
cd terraform
terraform apply
```
# Manual preparation steps
## DNS
The terraform will output the public ips of the provisioned boxes. Register the IP's on some DNS.
## NetworkManager
If you use CentOS, run 
```bash
yum install NetworkManager -y
systemctl start NetworkManager
``` 
on all boxes.
## Inventory
Prepare the hosts in `inventory.example`.

# Run openshift-ansible
Use open-shift ansible to deploy openshift. Tested on the release-3.9 branch.
```bash
ansible-playbook -i inventory.example openshift-ansible/playbooks/prerequisites.yml
ansible-playbook -i inventory.example openshift-ansible/playbooks/deploy-cluster.yml
```