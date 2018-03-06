ansible-cron
=========

Simple cron control based on jinja template and a for that looks for a dict variable.

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
  - { schedule: '0 7 * * *',  user: 'nobody', command: '/bin/true'     }
  - { schedule: '10 7 * * *', user: 'root',   command: 'sh /script.sh' }
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
      - { schedule: '0 7 * * *', user: 'nobody', command: '/bin/true' }

  roles:
    - kleinstuff.ansible-cron
```

License
-------

BSD

Author Information
------------------
https://rklein.com.br
