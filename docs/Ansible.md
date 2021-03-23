## Running Ansible Locally

This is useful for quickly testing/developing tasks.

Create a single yaml file with this structure:

```
- name: WIP installing dbtools
  hosts: localhost
  connection: local
  vars:
    foo: 0.7.2
    bar: baz
  tasks:
    - name: Check if foo is installed
      stat: path=/usr/local/bin/foo
      register: foo_installed
  ...
```

The `hosts` and `connection` keys are most important for local testing. Include any needed vars in the `vars` section.

Run it with `ansible-playbook path/to/file/above.yml`.

## Ansible Vault

* [ansible-vault-tools](https://github.com/building5/ansible-vault-tools) - provides useful `git diff` output for vault files and other handy tools like `git grep`. It also has a helper to encrypt your vault password file at rest.
