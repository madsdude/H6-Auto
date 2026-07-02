# H6-Auto

Automation repo for H6 NetBox, Semaphore and Ansible.

Flow:

```text
GitHub repo -> Semaphore job -> Ansible -> NetBox API
```

Semaphore Environment must contain:

```text
NETBOX_URL
NETBOX_TOKEN
NETBOX_VALIDATE_CERTS=false
ANSIBLE_HOST_KEY_CHECKING=False
```

Run order in Semaphore:

```text
1. playbooks/00_netbox_api_test.yml
2. playbooks/10_netbox_bootstrap.yml
3. playbooks/20_netbox_devices.yml
```

Install requirements on the Ansible/Semaphore host:

```bash
ansible-galaxy collection install -r requirements.yml
pip install -r requirements.txt
```

Edit NetBox source data here:

```text
data/netbox_h6_lab.yml
```
