os-upgrade
==========
[![Ansible Lint](https://github.com/oxivanisher/role-os_upgrade/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/oxivanisher/role-os_upgrade/actions/workflows/ansible-lint.yml)

Upgrades all OS packages to the latest version.
If the `os_upgrade_octoprint_api_key` variable is set, it checks for running 3d prints and excludes the system from updates if it is printing.

Role Variables
--------------

| Name                           | Comment                                                                                                                                                            | Default value |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------- |
| os_upgrade_clean_package_files | Should all downloaded package file be removed?                                                                                                                     | `true`        |
| os_upgrade_debian_mode         | Select the [package upgrade mode](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)                                             | `dist`        |
| os_upgrade_do_reboot           | Should the systems always be rebooted?                                                                                                                             | `false`       |
| os_upgrade_octoprint_api_key   | Octoprint API key                                                                                                                                                  | ``            |
| os_upgrade_reboot_if_required  | Only reboot the system if it is required.                                                                                                                          | `false`       |
| os_upgrade_suse_force_accept   | This forces zypper to accept new repo keys, replace files during upgrades and allows vendor changes.                                                               | `true`        |
| os_upgrade_suse_mode           | Select the target [package state](https://docs.ansible.com/ansible/latest/collections/community/general/zypper_module.html). Should be `latest` or `dist-upgrade`. | `latest`      |

**A note to reboot:** This variable controls if the system(s) will be rebooted. Default is no reboot, change `os_upgrade_do_reboot` to `true` to force reboots.


Dependencies
------------

None

Example Playbook
----------------

```yaml
- name: Raspberry Pi
  hosts: all
  collections:
    - oxivanisher.linux_base
  roles:
    - role: oxivanisher.linux_base.os_upgrade              # upgrade all packages
```

License
-------

BSD

Author Information
------------------

This role is part of the [oxivanisher.linux_base](https://galaxy.ansible.com/ui/repo/published/oxivanisher/linux_base/) collection, and the source for that is located on [github](https://github.com/oxivanisher/collection-linux_base).
