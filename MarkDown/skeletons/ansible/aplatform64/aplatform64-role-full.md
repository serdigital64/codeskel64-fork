---
title: "Ansible Role: serdigital64.X_COLLECTION_NAME_X.X_ROLE_NAME_X"
description: "X_ROLE_SHORT_DESCRIPTION_X"
authors:
  - SerDigital64
tags:
  - ansible
  - X_COLLECTION_NAME_X
  - linux
  - automation
---

# Ansible Role: serdigital64.X_COLLECTION_NAME_X.X_ROLE_NAME_X

## Purpose

X_ROLE_SHORT_DESCRIPTION_X

Supported features in the current version:

- Prepare environment for application deployment.
- Deploy application. Packages are defined in the variable `X_ROLE_NAME_X_profiles`.
- Control application subsystem services. Services are defined in the variable `X_ROLE_NAME_X_subsystems`.
- Configure application.
- Configure application subsystem server.
- Provision application components.
- Configure OS level firewall rules

The **X_ROLE_NAME_X** Ansible-Role is part of the [A:Platform64](https://github.com/serdigital64/aplatform64) project and is available in the [X_COLLECTION_NAME_X](../collections/X_COLLECTION_NAME_X.md) Ansible-Collection.

## Usage

The following example is an **Ansible Playbook** that includes all the supported features:

```yaml
{% include "../../collections/serdigital64/X_COLLECTION_NAME_X/playbooks/X_ROLE_NAME_X.yml" %}
```

The playbook can be run by executing:

```shell
# Set ANSIBLE_COLLECTIONS_PATHS to the default location. Change as needed.
ANSIBLE_COLLECTIONS_PATHS="${HOME}/.ansible/collections"
ansible-playbook "${ANSIBLE_COLLECTIONS_PATHS}/ansible_collections/serdigital64/X_COLLECTION_NAME_X/playbooks/X_ROLE_NAME_X.yml"
```

## Role Parameters

### Actions

- Use **action-parameters** to control what tasks are enabled for the role to execute.
- Parameters should be declared as task level vars as they are intented to be dynamic.

```yaml
X_ROLE_NAME_X:
  resolve_prereq:
  prepare:
  deploy:
  setup:
  control:
  provision:
```

| Parameter                    | Required? | Type    | Default | Purpose / Value                               |
| ---------------------------- | --------- | ------- | ------- | --------------------------------------------- |
| X_ROLE_NAME_X.resolve_prereq | no        | boolean | `false` | Enable automatic resolution of prequisites    |
| X_ROLE_NAME_X.prepare        | no        | boolean | `false` | Enable environment preparation                |
| X_ROLE_NAME_X.deploy         | no        | boolean | `false` | Enable installation of application packages   |
| X_ROLE_NAME_X.setup          | no        | boolean | `false` | Enable application configuration              |
| X_ROLE_NAME_X.control        | no        | boolean | `false` | Enable application subsystem service control  |
| X_ROLE_NAME_X.provision      | no        | boolean | `false` | Enable provisioning of application components |

### End State

- Use **end-state** parameters to define the target state after role execution.
- Parameters should be declared in **host_vars** or **group_vars** as they are intended to be permanent.

```yaml
X_ROLE_NAME_X_application:
  name:
  type:
  version:
  installed:
X_ROLE_NAME_X_subsystem:
  enabled:
  status:
X_ROLE_NAME_X_server_options:
  X_DEFAULT_SERVER_OPTION_X:
X_ROLE_NAME_X_paths:
  X_DEFAULT_PATH_X:
X_ROLE_NAME_X_users:
  X_DEFAULT_USER_X:
    name:
    group:
    home:
X_ROLE_NAME_X_firewall:
  zone:
```

| Parameter                                              | Required?    | Type       | Default                             | Purpose / Value                     |
| ------------------------------------------------------ | ------------ | ---------- | ----------------------------------- | ----------------------------------- |
| X_ROLE_NAME_X_application                              | yes(deploy)  | dictionary |                                     | Set application package end state   |
| X_ROLE_NAME_X_application.name                         | yes(deploy)  | string     | `"X_APP_ID_X"`                      | Select application package name     |
| X_ROLE_NAME_X_application.type                         | yes(deploy)  | string     | `"X_APP_TYPE_X"`                    | Select application package type     |
| X_ROLE_NAME_X_application.version                      | yes(deploy)  | string     | `"X_APP_VERSION_X"`                 | Select application package version  |
| X_ROLE_NAME_X_application.installed                    | yes(deploy)  | boolean    | `true`                              | Set application package end state   |
| X_ROLE_NAME_X_subsystem                                | yes(control) | dictionary |                                     | Set application subsystem end state |
| X_ROLE_NAME_X_subsystem.enabled                        | yes(control) | boolean    | `false`                             | Enable the subsystem?               |
| X_ROLE_NAME_X_subsystem.status                         | yes(control) | string     | `"stopped"`                         | Set the service state               |
| X_ROLE_NAME_X_server_options                           | yes(control) | dictionary |                                     | Set subsystem server options        |
| X_ROLE_NAME_X_server_options.X_DEFAULT_SERVER_OPTION_X | yes(control) | string     | `"X_DEFAULT_SERVER_OPTION_VALUE_X"` |                                     |
| X_ROLE_NAME_X_paths                                    | yes(prepare) | dictionary |                                     | Set paths                           |
| X_ROLE_NAME_X_paths.X_DEFAULT_PATH_X                   | yes(prepare) | string     | `"X_DEFAULT_PATH_VALUE_X"`          |                                     |
| X_ROLE_NAME_X_users                                    | yes(prepare) | dictionary |                                     | Define users                        |
| X_ROLE_NAME_X_users.X_DEFAULT_USER_X                   | yes(prepare) | dictionary |                                     | Define directory structure owner    |
| X_ROLE_NAME_X_users.X_DEFAULT_USER_X.name              | yes(prepare) | string     | `"X_DEFAULT_USER_NAME_X"`           | Set login name                      |
| X_ROLE_NAME_X_users.X_DEFAULT_USER_X.group             | yes(prepare) | string     | `"X_DEFAULT_USER_GROUP_X"`          | Set group name                      |
| X_ROLE_NAME_X_users.X_DEFAULT_USER_X.home              | yes(prepare) | string     | `"X_DEFAULT_USER_HOME_X"`           | Set home directory                  |
| X_ROLE_NAME_X_firewall                                 | no           | dictionary |                                     | OS Firewall options                 |
| X_ROLE_NAME_X_firewall.zone                            | yes          | string     | `"public"`                          | Name of the target zone             |

## Deployment

### OS Compatibility

- CentOS8
- OracleLinux8
- Ubuntu20
- Ubuntu21
- Fedora33
- Fedora35
- Debian10
- Debian11

### Dependencies

- Ansible Collections:
  - serdigital64.core

### Prerequisites

The Ansible engine must be already installed and configured for privileged access and remote execution.

In addition the following prerequisites can be automatically solved when running the playbook by setting the role action: `resolve_prereq: true`

- Package manager for the target application is installed and enabled.

### Installation Procedure

Manually install Ansible Collections from the Ansible Galaxy repository:

```shell
ansible-galaxy collection install serdigital64.X_COLLECTION_NAME_X
```

Automatic installation is also available by deploying [A:Platform64](https://aplatform64.readthedocs.io/en/latest/#deployment)

## Contributing

Help on implementing new features and maintaining the code base is welcomed.

Please see the [guidelines](../contributing/guidelines.md) for further details.

## Author

- [SerDigital64](https://serdigital64.github.io/)

## License

[GPL-3.0-or-later](https://www.gnu.org/licenses/gpl-3.0.txt)