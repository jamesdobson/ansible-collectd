collectd
==========

Ansible role to manage [collectd](https://collectd.org/).

*collectd* is a daemon that collects system performance statistics
periodically and provides mechanisms to store the data in a variety of
ways.

Requirements
------------

No external dependencies.

Role Variables
--------------

For details on configuring *collectd*, please refer to their
documentation:

* [Documentation](https://collectd.org/documentation.shtml)
* [collectd.conf](https://collectd.org/documentation/manpages/collectd.conf.5.shtml)
* [Wiki](https://collectd.org/wiki/index.php/Main_Page)

The following variables are used by this role to configure *collectd*:

* **collectd_packages**:  The default is to use the per-OS family
  default packages.  You can override this to install additional
  *collectd* packages.
* **collectd_conf_dir**:  Path to the directory that *collectd* will
  include configuration files from; defaults to `/etc/collectd.d`.
* **collectd_plugins**: A list of dictionaries that define plugins to
  load and configure.  Each element in the list must define the key `name`
  and *may* define the key `conf`.  The key `conf` is used to provide
  plugin specific configuration.  Examples:
```
collectd_plugins:
  - name: syslog
  - name: disk
    conf: |
      Disk "vda"
      IgnoreSelected false
```

Dependencies
------------

No dependency on other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - { role: sfromm.collectd }

License
-------

GPLv2

Author Information
------------------

See https://github.com/sfromm
