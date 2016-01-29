Install Consul Cluster:
===============================

Provision aws ec2 nodes for Consul cluster:

```
ansible-playbook --private-key ~/.ssh/<your-key>.pem -i hosts playbooks/1_consul-aws-provision.yml -e key_name="<your-key-name>"
```

Install Consul cluster:

```
ansible-playbook --private-key ~/.ssh/<your-key>.pem -i playbooks/consul.hosts playbooks/2_consul-aws-install.yml -e datacenter=test-dc
```
