# bouncmpe.automated.manage_users

## Requirements

None.

## Role Variables

```yaml
# List of user groups to be created
usergroups: []
# List of users to be created/managed
users: []
```

## Default Variables

```yaml
default_user_directory: /home
default_user_state: present
default_user_remove: false
default_user_create_home: true
default_user_groups: []
default_user_shell: /bin/bash
```

## Example Playbook

```yaml
# users.yml
---
- name: Add and manage users on hosts
  hosts: localhost
  become: true

  roles:
    - bouncmpe.automated.manage_users

  # Describe usergroups and users in the following
  vars:
    usergroups: ["sudo", "users"] # List of user group names
    users:
      - name: dogan.ulus
        groups: ["sudo", "users"]
        ssh_import_id:
          - gh:doganulus

      - name: dulus
        groups: ["users"]
        ssh_import_id:
          - gh:doganulus
```

## Dependencies

None.
