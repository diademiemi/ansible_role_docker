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
- Debian 12
- EL 8 (Tested on Rocky Linux 8)
- EL 9 (Tested on Rocky Linux 9)
- Fedora 38
- openSUSE Leap 15.5

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
`docker_el_os_name` | See [vars/](./vars) | Repository name for RHEL-based Linux operating systems
`docker_install_pip_packages` | `true` | Whether to the Docker Python package
`docker_pip_global_packages` | See [vars/default.yml](./vars/default.yml) | Global Python packages to install
<!--
`variable` | `default` | Variable example
`long_variable` | See [defaults/main.yml](./defaults/main.yml) | Variable referring to defaults
`distro_specific_variable` | See [vars/debian.yml](./vars/debian.yml) | Variable referring to distro-specific variables
-->

Dependencies
------------
<!-- List dependencies on other roles or criteria -->
None
`diademiemi.python` collection when `docker_install_pip_packages` is `true`

Example Playbook
----------------

```yaml
- name: Use diademiemi.docker role
  hosts: "{{ target | default('docker') }}"
  roles:
    - role: "diademiemi.docker"
      vars:
        __role_action: "setup"  # Variable to control which tasks are ran, default is "setup"
        # __role_action: "uninstall_old" # Uncomment to uninstall old packages
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

This repository comes with Molecule that run in Podman on the supported platforms.
Install Molecule by running

```bash
pip3 install -r requirements.txt
```

Run the tests with

```bash
molecule test
```

These tests are automatically ran by GitHub Actions on push. If the tests are successful, the role is automatically published to Ansible Galaxy.
