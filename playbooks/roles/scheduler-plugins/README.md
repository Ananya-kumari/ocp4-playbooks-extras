scheduler-plugins
=========

The role allows users to define which CLI plugins to deploy and test via the deploy_cli_plugins variable, and it ensures all prerequisites and dependencies are installed before deployment.

The OCP CLI-Plugins role automates the installation, configuration, and testing of several CLI plugins for OpenShift. By configuring the deploy_cli_plugins variable, users can specify which plugins to deploy and test, and the role will take care of all necessary tasks.


Requirements
------------

- OCP 4.x healthy cluster on PowerVC.

Role Variables
--------------

| Variable                     | Required | Default        | Comments                                                  |
|------------------------------|----------|----------------|-----------------------------------------------------------|
| scheuler_plugins_enabled     | no       | false          | Set it to true to run this playbook                       |
| enable_cli_plugins_test      | no       | true           | Set to true to enable custom CLI plugin testing. |
| deploy_cli_plugins           | yes       | []            | List of CLI plugin names to be deployed and tested. Valid values: ["custom", "krew", "mirror", "compliance"]. Empty list will skip deployment.  |
| user_custom_plugin           | no       | ""             | File name of the user-defined custom CLI plugin (e.g., oc-my-plugin.sh). A sample plugin oc-test-plugin.sh is included in the role. |
| golang_tar_url               | no       | ""             | Golang tarball URL for ppc64le architecture (version >= 1.18). Default URL is provided in defaults/main.yaml.|


Dependencies
------------

- None

Example Playbook
----------------
```
---
- name: OCP CLI-Plugins Test Suite
  hosts: bastion
  roles:
    - ocp-cli-plugins
```

License
-------

See LICENCE.txt

Author Information
------------------

ananya.kumari@ibm.com

