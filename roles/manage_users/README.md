# bouncmpe.automated.manage_users

## Description

This is an Ansible playbook, which manages user accounts and their SSH keys, as well as sudo access for those users.

## Example Playbook

```yaml
# users.yml
---
- name: Manage users on all hosts
  hosts: all
  become: true

  roles:
    - bouncmpe.automated.manage_users

  # Describe usergroups and users in the following
  vars:
    config:
      groups: ["sudo", "faculty"]
      users:
        - name: dogan.ulus
          groups: ["sudo", "faculty"]
          ssh_import_id:
            - gh:doganulus # get public ssh keys from https://github.com/doganulus.keys
          ssh_authorized_keys:
            - <my public ssh key>
          sudoers:
            nopassword: true # no password for sudo

        - name: dulus
          lock_passwd: false # not recommended
          passwd: <my hashed password> # not recommended
          sudoers:
            commands:
              - /usr/bin/ls # allow: sudo ls
              - /usr/bin/cat # allow: sudo cat
            nopassword: false # require password for sudo
```
