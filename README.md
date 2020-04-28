Ansible Role flxpeters.tomcat8
=========

[![Build Status](https://travis-ci.org/FlxPeters/ansible-role-tomcat8.svg?branch=master)](https://travis-ci.org/FlxPeters/ansible-role-tomcat8)

Install Tomcat 8 or 9 on Ubuntu >= 16.04, Debian, CentOS,   from archive with systemd

Requirements
------------

This role depends on existing Java installation. The java installation is not part of this role.
You must define the JAVA_HOME in the `tomcat_java_home` variable.

Role Variables
--------------

`tomcat_java_home` The path to your java installation. This variable is required in the systemd service file.


# Directory to store files downloaded for Java installation on the remote box
tomcat_download_dir: "{{ x_ansible_download_dir | default(ansible_env.HOME + '/.ansible/tmp/downloads') }}"

# Location Tomcat installations packages can be found on the local box
# local packages will be uses in preference to downloading new packages.
tomcat_local_archive_dir: '{{ playbook_dir }}/files'

# Wether to use installation packages in the local archive (if available)
# default is false
tomcat_use_local_archive: true

# File name for the Tomcat redistributable installation file
tomcat_redis_filename: apache-tomcat-9.0.34.tar.gz

To use local files, add the tomcat tgz into ./files/
And add these variables 
tomcat_archive_name: "apache-tomcat-9.0.34"
tomcat_use_local_archive: true
tomcat_redis_filename: apache-tomcat-9.0.34.tar.gz


Dependencies
------------

A running Java installation like open-jdk-8.

Installation of the Role
----------------

`ansible-galaxy install pulse-mind.ansible-role-tomcat`

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: pulse-mind.ansible-role-tomcat, tomcat_java_home: /path/to/java/jre }

For assistance on getting location of java_home from your server check stackoverflow answer [here](https://stackoverflow.com/a/23427862/5128251)

Tomcat service is stored into /etc/systemd/system/tomcat.service

Test
----

This roles uses Molecule to test. You can run the tests like this:

    molecule test

License
-------

MIT / BSD
