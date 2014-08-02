# Ansible Fail2ban Role

[![Build Status](https://travis-ci.org/weareinteractive/ansible-role-fail2ban.png?branch=master)](https://travis-ci.org/weareinteractive/ansible-role-fail2ban)
[![Stories in Ready](https://badge.waffle.io/weareinteractive/ansible-role-fail2ban.svg?label=ready&title=Ready)](http://waffle.io/weareinteractive/ansible-role-fail2ban)

> `fail2ban` is an [ansible](http://www.ansible.com) role which: 
> 
> * installs fail2ban

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
$ git clone https://github.com/weareinteractive/ansible-role-fail2ban.git
```

## Variables

```
# Start on boot
fail2ban_service_enabled: yes
# Current state: started, stopped
fail2ban_service_state: started
```

## Example playbook

```
- host: all
  roles: 
    - franklinkim.fail2ban
  vars:
    fail2ban_service_state: started
    fail2ban_service_enabled: yes
```

## Testing

```
$ git clone https://github.com/weareinteractive/ansible-role-fail2ban.git
$ cd ansible-role-fail2ban
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
