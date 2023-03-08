# Dependencies

## Install Ansible
The example below is for RHEL/CentOS 8

```
sudo dnf -y install python3-pip
sudo pip3 install --upgrade pip
pip3 install ansible --user
```

## Clone Repo
```
git clone https://github.com/Sapphire-Health/ansible-vmware.git
cd ansible-vmware
```

## Install Dependencies
```
ansible-galaxy collection install -r collections/requirements.yml
yum install python3-pyvmomi
```

## Set environment variables
In Ansible Tower these values are configured using a "VMware vCenter" credential resource.

```
export VMWARE_HOST=vcenterhostname.fqdn.com
export VMWARE_USER=domain\\username
export VMWARE_PASSWORD=password
```

## Get ESXi Inventory in YAML format
```
ansible-inventory -i inventory_esxi_vmware.yml --list -y
```

## List all VMs on ESXi hosts using dynamic inventory
```
ansible-playbook -i inventory_esxi_vmware.yml -e match_host=wjm* esxi/get_vms.yml
```