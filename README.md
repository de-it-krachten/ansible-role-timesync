[![CI](https://github.com/de-it-krachten/ansible-role-timesync/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-timesync/actions?query=workflow%3ACI)


# ansible-role-timesync

Configure time synchronization based upon timesync


Platforms
--------------

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- RockyLinux 8
- AlmaLinux 8<sup>1</sup>
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS

Note:
<sup>1</sup> : no automated testing is performed on these platforms

Role Variables
--------------
<pre><code>
# packages that need to be present
timesync_packages:
  - systemd-timesyncd

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


Example Playbook
----------------

<pre><code>
- name: sample playbook for role 'timesync'
  hosts: all
  vars:
    timesync_timezone: UTC
    timesync_ntp_servers: ['0.nl.pool.ntp.org', '1.nl.pool.ntp.org', '2.nl.pool.ntp.org', '3.nl.pool.ntp.org']
  tasks:
    - name: Include role 'timesync'
      include_role:
        name: timesync
</pre></code>
