[![CI](https://github.com/de-it-krachten/ansible-role-timesync/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-timesync/actions?query=workflow%3ACI)


# ansible-role-timesync

Configure time synchronization based upon timesync



## Dependencies

#### Roles
None

#### Collections
- community.general
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- AlmaLinux 8
- AlmaLinux 9
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 35
- Fedora 36

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# packages that need to be present
timesync_packages:
  - systemd-timesyncd

# should obsolete packages be uninstalled
timesync_packages_uninstall: false

# Packages that can be removed
timesync_packages_obsolete:
  - chrony
  - ntp

# Obsolete services
timesync_services_obsolete:
  - chrony
  - chronyd
  - ntp
  - ntpd

# Time zone (eg 'Europe/Amsterdam')
# Use value 'unchanged' to leave it unchanged
timesync_timezone: ""

# Ensure hwclock is set to UTC or local time
# options : local, UTC
timesync_hwclock: null

# List of primary NTP servers
timesync_ntp_servers: []

# List of fallback NTP servers
timesync_fallback_ntp_servers:
  - 0.pool.ntp.org
  - 1.pool.ntp.org
  - 2.pool.ntp.org
  - 3.pool.ntp.org

# Additional options (as key/value pairs)
timesync_options: {}
</pre></code>


### vars/Ubuntu-18.yml
<pre><code>
# packages that should be installed
timesync_packages: []
</pre></code>

### vars/Fedora.yml
<pre><code>
# packages that need to be present
timesync_packages:
  - systemd-udev
</pre></code>

### vars/family-RedHat.yml
<pre><code>

</pre></code>

### vars/Debian-10.yml
<pre><code>
# packages that should be installed
timesync_packages: []
</pre></code>

### vars/family-Debian.yml
<pre><code>

</pre></code>

### vars/family-RedHat-7.yml
<pre><code>
# packages that should be installed
timesync_packages: []
</pre></code>



## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'timesync'
  hosts: all
  become: "{{ molecule['converge']['become'] | default('yes') }}"
  vars:
    timesync_timezone: UTC
    timesync_ntp_servers: ['0.nl.pool.ntp.org', '1.nl.pool.ntp.org', '2.nl.pool.ntp.org', '3.nl.pool.ntp.org']
  tasks:
    - name: Include role 'timesync'
      ansible.builtin.include_role:
        name: timesync
</pre></code>
