# Ansible role for installing check_mk agent on hosts for use with OMD servers.

Role installs check_mk agent from rpm downloaded from OMD server, configures allowed hosts in xinetd service, adds (downloads from OMD server) selected check_mk plugins.

Required variables:
  - check_mk_server_url
  - check_mk_package_file
  - omdistro_site
  - monitoring_allowed_hosts

Playbook example:

```yaml
---
- name: Install and configure check_mk agent
  hosts: all
  become: yes
  roles:
    - role: check-mk-agent
      check_mk_server_url: "https://monitoring.example.com"
      check_mk_package_file: "check-mk-agent-1.2.6p12-1.noarch.rpm"
      omdistro_site: "omdsite"
      when: monitoring is defined and monitoring == "true"
```
