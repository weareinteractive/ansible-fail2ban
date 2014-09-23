# Ansible Fail2ban Role

[![Build Status](https://travis-ci.org/weareinteractive/ansible-fail2ban.png?branch=master)](https://travis-ci.org/weareinteractive/ansible-fail2ban)
[![Stories in Ready](https://badge.waffle.io/weareinteractive/ansible-fail2ban.svg?label=ready&title=Ready)](http://waffle.io/weareinteractive/ansible-fail2ban)

> `fail2ban` is an [ansible](http://www.ansible.com) role which: 
> 
> * installs fail2ban
> * configures jail.local
> * configures service

## Installation

Using `ansible-galaxy`:

```
$ ansible-galaxy install franklinkim.fail2ban
```

Using `arm` ([Ansible Role Manager](https://github.com/mirskytech/ansible-role-manager/)):

```
$ arm install franklinkim.fail2ban
```

Using `git`:

```
$ git clone https://github.com/weareinteractive/ansible-fail2ban.git
```

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```
# fail2ban_jail:
#   ssh:
#     enabled: true
#     port: ssh
#     filter: sshd
#     logpath: /var/log/auth.log
#     maxretry: 6
# fail2ban_jail_template: templates/jail.local.j2
# 

# start on boot
fail2ban_service_enabled: yes
# current state: started, stopped
fail2ban_service_state: started
# jail.local config variables
fail2ban_jail: {}
# jail.local template to install, relative to the ansible repository root
fail2ban_jail_template:
```

## Handlers

These are the handlers that are defined in `handlers/main.yml`.

* `restart fail2ban` 

## Example playbook

```
- host: all
  roles: 
    - franklinkim.fail2ban
  vars:
    fail2ban_service_state: started
    fail2ban_service_enabled: yes
    fail2ban_jail_local: files/etc-fail2ban-jail.local.j2
```

With the `files/etc-fail2ban-jail.local.j2` i.e. looking like:

```
# {{ ansible_managed }}

[ssh-iptables]
#enabled  = false
enabled  = true
filter   = sshd
action   = iptables[name=SSH, port=ssh, protocol=tcp]
#          mail-whois[name=SSH, dest=yourmail@mail.com]
#logpath  = /var/log/sshd.log
logpath  = /var/log/auth.log
maxretry = 5
```

## Testing

```
$ git clone https://github.com/weareinteractive/ansible-fail2ban.git
$ cd ansible-fail2ban
$ vagrant up
```

## Contributing

In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License
Copyright (c) We Are Interactive under the MIT license.
