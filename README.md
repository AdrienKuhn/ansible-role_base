Ansible Base role
=========

This role ensure basic requirements are met:
- Install packages updates
- Install basic packages
  - aptitude
  - curl
  - debian-goodies
  - git
  - htop
  - locales
  - rsync
  - secure-delete
  - tree
  - vim
  - wget
- Enable/Disable IPV6
- Configure timezone and NTP
- Create and configure a Swapfile

Requirements
------------

None

Supported distributions
-----------------------

- Debian 8
- Debian 9

Role Variables
--------------

```yml
##
# Date & Time
##

# Timezone
timezone: UTC

# NTP server
ntp_server: pool.ntp.org

##
# Swap
##

# Path to swapfile
swap_path: /var/swapfile

# Hosts with low RAM may need to use a small bs size
dd_bs_size_mb: 1

# Count of how many passes dd should make at bs size
swap_count: 1024

# how often swap is utilized, 60 is good for desktops, 10 is good for VPS
swappiness: 10

# How often inode info is removed from cache. Usually a frequent and costly lookup if not cached
vfs_cache_pressure: 50

##
# Base packages
##

# Packages to install by default on all servers
default_packages:
  - aptitude
  - curl
  - debian-goodies
  - git
  - htop
  - rsync
  - secure-delete
  - tree
  - vim
  - wget
  - locales

##
# Networking
##

# IPv6
# Should be set to false if fail2ban 0.10 (with IPv6 support) is not available on server
ipv6: true
```

Dependencies
------------

None

Tests
-----

```
$ cd tests
$ vagrant up --provision # or vagrant provision if the VM is already up
```