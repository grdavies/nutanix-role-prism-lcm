Nutanix Role for Prism LCM Software & Firmware Updates
=========

This Ansible role invokes LCM to perform an inventory operation followed by software and firmware updates if necessary.


Role Variables
--------------

| Variable                         | Required | Default | Choices                                                                                | Comments                                                                                                                                                                                                     |
|----------------------------------|----------|---------|----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| validate_certs                   | no       | no      |                                                                                        | Whether to check if Prism UI certificates are valid.                                                                                                                                                         |
| nutanix_lcm_run_inventory        | no       | True    | True or False                                                                          | Whether to run an inventory prior to installing updates.                                                                                                                                                     |
| nutanix_lcm_run_software_updates | no       | True    | True or False                                                                          | Whether to install software updates.                                                                                                                                                                         |
| nutanix_lcm_software_to_update   | no       | []      | ["NCC", "Cluster Maintenance Utilities", "Foundation", "AHV hypervisor", "AOS", "FSM"] | If not defined then all available software updates will be installed. If one or more software choices are provided then only they will be updated, if not choices are provided all software will be updated. |
| nutanix_lcm_run_firmware_updates | no       | True    | True or False                                                                          | Whether to install firmware updates.                                                                                                                                                                         |
| nutanix_lcm_run_precheck         | no       | True    | True or False                                                                          | Whether to run a LCM precheck prior to installing updates.                                                                                                                                                   |
| nutanix_lcm_retries              | no       | 5       |                                                                                        | Number of progress checks                                                                                                                                                                                    |
| nutanix_lcm_delay                | no       | 300     |                                                                                        | Progress check interval                                                                                                                                                                                      |


Dependencies
------------

- grdavies.nutanix_role_prism_init_api


Example Playbook
----------------

This example playbook will invoke LCM on a specific cluster running only a software upgrade for "NCC"

```
- hosts: localhost
 roles:
   - role: grdavies.nutanix-role-prism-lcm
 vars:
   nutanix_host: 10.38.185.37
   nutanix_username: admin
   nutanix_password: nx2Tech165!
   nutanix_lcm_run_firmware_updates: False
   nutanix_lcm_software_to_update:
     - NCC
```
License
-------

See LICENSE.md

Author Information
------------------

Ross Davies
