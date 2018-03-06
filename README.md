[![Build Status](https://travis-ci.org/kleinstuff/ansible-cron.png)](https://travis-ci.org/kleinstuff/ansible-cron)

ansible-cron
=========

Simple cron control based on jinja template and a for loop that looks for a list variable with all the jobs.
This role was made to be as simple as possible to migrate crontab files to Ansible.

Requirements
------------

Works only on el7 for now, but its easy to be updated to work with other systems.
If you need, drop a PR or an ISSUE.

Role Variables
--------------

### ansible_cron__head
The head of the confile, defaults to:
```
  SHELL=/bin/bash
  PATH=/sbin:/bin:/usr/sbin:/usr/bin
  MAILTO=root

```

### ansible_cron__jobs
The actual jobs, its required and you should use like this:
```yaml
ansible_role_cron__jobs:
  - '0 7 * * *  nobody  /bin/true'
  - '10 7 * * * root    sh /script.sh'
```

Dependencies
------------

There are no deps.

Example Playbook
----------------
```yaml
---
- hosts: all

  vars:
    ansible_role_cron__jobs:
      - '0 7 * * * nobody /bin/true'

  roles:
    - kleinstuff.ansible-cron
```

License
-------

BSD

Author Information
------------------
https://rklein.com.br
