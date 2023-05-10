Ansible Role Docker
=========

[![Molecule Test](https://github.com/diademiemi/ansible_role_docker/actions/workflows/molecule.yml/badge.svg)](https://github.com/diademiemi/ansible_role_docker/actions/workflows/molecule.yml)

This is an Ansible role to install and configure docker.

Include more information about docker in this section.

Requirements
------------
These platforms are supported:
- Ubuntu 20.04  
- Ubuntu 22.04  
- Debian 10  
- Debian 11  
- EL 8 (Tested on Rocky Linux 8)  
- EL 9 (Tested on Rocky Linux 9)  
- Fedora 38  

<!-- 
- List hardware requirements here  
-->

Role Variables
--------------

Variable | Default | Description
--- | --- | ---
`docker_add_users_to_group` | `true` | Whether to add users to `docker` group
`docker_users` | `[{{ ansible_user_id }}]` | Users to add to Docker group
`docker_packages` | See [vars/](./vars) | Packages to install
`docker_uninstall_old_packages` | See [vars/](./vars) | Which packages to install when `__role_action` is `uninstall_old`
`docker_el_os_name` | See [vars/](./vars) | Repository name for Enterprise Linux operating systems
<!--
`variable` | `default` | Variable example
`long_variable` | See [defaults/main.yml](./defaults/main.yml) | Variable referring to defaults
`distro_specific_variable` | See [vars/debian.yml](./vars/debian.yml) | Variable referring to distro-specific variables
-->

Dependencies
------------
<!-- List dependencies on other roles or criteria -->
None

Example Playbook
----------------

```yaml
    - role: "diademiemi.docker"
      vars:
        __role_action: # Variable to control which tasks are ran
          # - "uninstall_old" # Uncomment to uninstall old packages
          - "setup" # Default if none is given
      tags: ['diademiemi', 'docker', 'setup']    ```

```

License
-------

MIT

Author Information
------------------

- diademiemi (@diademiemi)

Role Testing
------------

This repository comes with Molecule tests for Docker on the supported platforms.
Install Molecule by running
```bash
pip3 install -r requirements.txt
```

Run the tests with
```bash
molecule test
```

These tests are automatically ran by GitHub Actions on push. If the tests are successful, the role is automatically published to Ansible Galaxy.

