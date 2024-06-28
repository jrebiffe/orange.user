# orange.user

Manage user accounts via NETCONF and ietf-system YANG module

Role Variables
--------------

This demonstrator use only 2 settable variables: `user_name` and `user_password`.

| Parameter       | Type   | Required | Example       | Comments                                                             |
|-----------------|--------|----------|---------------|----------------------------------------------------------------------|
| `user_name`     | string | Yes      | testuser1     | Name of the user to create, remove or modify.                        |
| `user_password` | string | Yes      | TopSecret123* | If provided, set the user’s password to the provided encrypted hash. |


Dependencies
------------

The [`ansible.netcommon`](https://galaxy.ansible.com/ui/repo/published/ansible/netcommon/)
collection is required, because the module
[`netconf_config`](https://docs.ansible.com/ansible/latest/collections/ansible/netcommon/netconf_config_module.html)
is used.

Example Playbook
----------------

Here is a fully functional playbook, but insecure because password are in cleartext:

```yaml
---
- name: Update the password of testuser1
  hosts: my_microwave_ne

  roles:

    - role: orange.user
      vars:
        user_name: testuser1
        user_password: TopSecret123*
```

The [test_user_ansible](https://github.com/jrebiffe/test_user_ansible) repository
usable as project on AWX.

License
-------

MIT

Author Information
------------------

Jean Rebiffe, Orange Innovation Networks, 2024
