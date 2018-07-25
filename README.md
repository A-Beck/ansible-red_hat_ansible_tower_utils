# Ansible Tower Utilities

Collection of Playbooks and Tasks to Automate Ansible Tower Management on RHEL.

Minimum Required Ansible Version: Ansible 2.5

## Playbooks

There are several playbooks included in this repository. To run the playbooks in this repository, there is the assumption of using an Ansible Tower installation inventory file. For an example of what such an inventory file looks like, please see the inventory file included in this repository.

All playbooks are stored in the playbooks directory. However, all ansible commands should be invoked from the root of the repository. See the example commands provided in this document for correct usage.

### configure-tower.yml

Pushes customized configuration files to tower nodes, followed by restart of tower services.

#### Example Playbook Command

```
ansible-playbook -i ./inventory ./playbooks/configure-tower.yml
```

### patch-tower.yml

Perform RHEL OS updates on Tower nodes.

#### Example Playbook Command

```
ansible-playbook -i ./inventory ./playbooks/patch-tower.yml
```

### rolling-tower-restart.yml

Restart non-DB Ansible Tower Services on all nodes in a rolling fashion.

#### Example Playbook Command

```
ansible-playbook -i ./inventory ./playbooks/rolling-tower-restart.yml
```

### update-ansible-engine.yml

Update the Ansible Engine package on RHEL Tower nodes.

[Current Tower and Engine compatibility](https://access.redhat.com/articles/3382771)

##### Options
| parameter        | required | default | comments
|------------------|----------|---------|--------------------------------------------------------------------
| ansible\_version | No       |   2.5   | Major.Minor version of Ansible. Must be in format x.y, i.e 2.6. Determines the Ansible Engine RHSM repository to enable.

#### Example Playbook Command

```
ansible-playbook -i ./inventory ./playbooks/update-ansible-engine.yml -e "ansible_version=2.6"
```
