Ansible Role: rTorrent
=====
[![Build Status](https://travis-ci.org/cmprescott/ansible-role-rtorrent.svg?branch=master)](https://travis-ci.org/cmprescott/ansible-role-rtorrent)

Ansible role to install and configure rTorrent.

Requirements
------------

Default package manager of **apt**, **yum**, or **pkgng**. 

Role Variables
--------------

```yaml
# ----- bandwidth settings -----
rtorrent_min_peers: 40
rtorrent_max_peers: 100
rtorrent_min_peers_seed: 10
rtorrent_max_peers_seed: 50
rtorrent_max_uploads: 15
rtorrent_download_rate: 0
rtorrent_upload_rate: 0

# ----- directory settings -----
rtorrent_directory_download: ~/rtorrent/download
rtorrent_directory_session: ~/rtorrent/.session
rtorrent_directory_watch: ~/rtorrent/watch

# ----- network settings -----
rtorrent_port_range: 49164-49164
rtorrent_port_random: "no"

# ----- schedule settings -----
rtorrent_schedule_watch_directory: watch_directory,5,5,load_start={{ rtorrent_directory_watch }}/*.torrent
rtorrent_schedule_untied_directory: untied_directory,5,5,stop_untied=

# ----- torrent settings -----
rtorrent_check_hash: "no"
rtorrent_use_udp_trackers: "yes"
rtorrent_encryption: allow_incoming,enable_retry,prefer_plaintext
rtorrent_dht: "off"
rtorrent_dht_port: 6881
rtorrent_peer_exchange: "yes"

# ----- other settings -----
#  (can break rtorrent when misconfigured)
rtorrent_other_settings: []
# Example
#    - scgi_port = 127.0.0.1:5000 
```

Dependencies
------------

None

Example Playbook
-------------------------

1) Install rTorrent with default settings

```yaml
- hosts: servers-torrent
  roles:
    - role: cmprescott.rTorrent
```

2) Install rTorrent with custom settings

```yaml
- hosts: servers-torrent
  roles:
    - role: cmprescott.rTorrent
      rtorrent_min_peers: 0
      rtorrent_max_peers: 1000
```

License
-------

BSD

Author Information
------------------

Prescott Chris

