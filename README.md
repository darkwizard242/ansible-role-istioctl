[![build-test](https://github.com/darkwizard242/ansible-role-istioctl/workflows/build-and-test/badge.svg?branch=master)](https://github.com/darkwizard242/ansible-role-istioctl/actions?query=workflow%3Abuild-and-test) [![release](https://github.com/darkwizard242/ansible-role-istioctl/workflows/release/badge.svg)](https://github.com/darkwizard242/ansible-role-istioctl/actions?query=workflow%3Arelease) ![Ansible Role](https://img.shields.io/ansible/role/d/darkwizard242/istioctl) [![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-istioctl&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=ansible-role-istioctl) [![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-istioctl&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=ansible-role-istioctl) [![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-istioctl&metric=security_rating)](https://sonarcloud.io/dashboard?id=ansible-role-istioctl) ![GitHub tag (latest SemVer)](https://img.shields.io/github/tag/darkwizard242/ansible-role-istioctl?label=release) ![GitHub repo size](https://img.shields.io/github/repo-size/darkwizard242/ansible-role-istioctl?color=orange&style=flat-square)

# Ansible Role: istioctl

Role to install (_by default_) [istioctl](https://github.com/istio/istio) on **Debian/Ubuntu** and **EL** systems. **istioctl** is a the CLI for Istio, an open source service mesh for Kubernetes.

## Requirements

None.

## Role Variables

Available variables are listed below (located in `defaults/main.yml`):

### Variables list:

```yaml
istioctl_app: istioctl
istioctl_version: 1.22.3
istioctl_os: linux
istioctl_architecture_map:
  amd64: amd64
  arm: arm64
  x86_64: amd64
  armv6l: armv6
  armv7l: armv7
  aarch64: arm64
  32-bit: "386"
  64-bit: amd64
istioctl_dl_url: https://github.com/istio/istio/releases/download/{{ istioctl_version }}/istio-{{ istioctl_version }}-{{ istioctl_os }}-{{ istioctl_architecture_map[ansible_architecture] }}.tar.gz
istioctl_bin_path: /usr/local/bin
istioctl_file_owner: root
istioctl_file_group: root
istioctl_file_mode: '0755'
```

### Variables table:

Variable                  | Description
------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------
istioctl_app              | Defines the app to install i.e. **istioctl**
istioctl_version          | Defined to dynamically fetch the desired version to install. Defaults to: **1.22.3**
istioctl_os               | Defines os type. Used for obtaining the correct type of binaries based on OS type. Defaults to: **linux**
istioctl_architecture_map | Defines os architecture. Used to set the correct type of binaries based on OS System Architecture.
istioctl_dl_url           | Defines URL to download the istioctl binary from.
istioctl_bin_path         | Defined to dynamically set the appropriate path to store istioctl binary into. Defaults to (as generally available on any user's PATH): **/usr/local/bin**
istioctl_file_owner       | Owner for the binary file of istioctl.
istioctl_file_group       | Group for the binary file of istioctl.
istioctl_file_mode        | Mode for the binary file of istioctl.

## Dependencies

None

## Example Playbook

For default behaviour of role (i.e. installation of **istioctl**) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.istioctl
```

For customizing behavior of role (i.e. specifying the desired **istioctl** version) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.istioctl
  vars:
    istioctl_version: 1.17.1
```

For customizing behavior of role (i.e. placing binary of **istioctl** package in different location) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.istioctl
  vars:
    istioctl_bin_path: /bin/
```

## License

[MIT](https://github.com/darkwizard242/ansible-role-istioctl/blob/master/LICENSE)

## Author Information

This role was created by [Ali Muhammad](https://www.alimuhammad.dev/).
