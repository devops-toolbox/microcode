Role Name
=========

microcode: Microcode

[![Build Status](https://travis-ci.org/cmihai-ansible/microcode.svg?branch=master)](https://travis-ci.org/cmihai-ansible/microcode)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.microcode](https://galaxy.ansible.com/devops-toolbox.microcode)

```bash
ansible-galaxy install devops-toolbox.microcode
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
microcode_packages_state: present
microcode_remove_packages: true
microcode_enable_service: true
microcode_enable_selinux: true
microcode_copy_templates: true
microcode_firewall_configure: true
microcode_firewall_rules:
  - service: ssh
  - port: 3389
microcode_users:
  - user: devops
    group: docker
microcode_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install microcode on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: microcode is configured
      import_role:
        name: devops-toolbox.microcode
      vars:
        microcode_packages_state: present
        microcode_remove_packages: true
        microcode_enable_service: true
        microcode_enable_selinux: true
        microcode_copy_templates: true
        microcode_firewall_configure: true
        microcode_firewall_rules:
          - service: ssh
          - port: 3389
        microcode_users:
          - user: devops
            group: docker
        microcode_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: microcode
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
