# [ulimit](#ulimit)

Configure ulimit on your system.

|GitHub|GitLab|Quality|Downloads|Version|Issues|Pull Requests|
|------|------|-------|---------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-ulimit/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-ulimit/actions)|[![gitlab](https://gitlab.com/buluma/ansible-role-ulimit/badges/master/pipeline.svg)](https://gitlab.com/buluma/ansible-role-ulimit)|[![quality](https://img.shields.io/ansible/quality/57987)](https://galaxy.ansible.com/buluma/ulimit)|[![downloads](https://img.shields.io/ansible/role/d/57987)](https://galaxy.ansible.com/buluma/ulimit)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-ulimit.svg)](https://github.com/buluma/ansible-role-ulimit/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-ulimit.svg)](https://github.com/buluma/ansible-role-ulimit/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-ulimit.svg)](https://github.com/buluma/ansible-role-ulimit/pulls/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.ulimit
      ulimit_items:
        - limit_item: nofile
          domain: root
          limit_type: soft
          value: 1048576
        - limit_item: nproc
          domain: root
          limit_type: soft
          value: 1024
        - limit_item: nproc
          domain: root
          limit_type: hard
          value: 2048
```

The machine needs to be prepared. In CI this is done using `molecule/default/prepare.yml`:
```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
```


## [Role Variables](#role-variables)

The default values for the variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for ulimit

# Set the default domain. This can be overwritten per item.
ulimit_domain: '*'

# Set the limit type. This can be overwritten per item.
ulimit_limit_type: soft

# Set the file where to write to.
ulimit_dest: /etc/security/limits.conf

# Should a backup of limits.conf be created on changes?
ulimit_backup: yes
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-ulimit/blob/main/requirements.txt).

## [Status of used roles](#status-of-requirements)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab ](https://gitlab.com/buluma/ansible-role-bootstrap/badges/main/pipeline.svg)](https://gitlab.com/buluma/ansible-role-bootstrap)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-ulimit/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|amazon|Candidate|
|el|8|
|debian|all|
|fedora|all|
|opensuse|all|
|ubuntu|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

## [Exceptions](#exceptions)

Some roles can't run on a specific distribution or version. Here are some exceptions.

| variation                 | reason                 |
|---------------------------|------------------------|
| Alpine | directory /etc/security is not writable |


If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-ulimit/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-ulimit/blob/master/CHANGELOG.md)

## [License](#license)

Apache-2.0

## [Author Information](#author-information)

[Michael Buluma](https://buluma.github.io/)
