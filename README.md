Ansible Role flxpeters.tomcat8
=========

[![Build Status](https://travis-ci.org/FlxPeters/ansible-role-tomcat8.svg?branch=master)](https://travis-ci.org/FlxPeters/ansible-role-tomcat8)

Install Tomcat 8 on Ubuntu >= 16.04 from archive with systemd

Requirements
------------

This role depends on existing Java installation. The java installation is not part of this role.
You must define the JAVA_HOME in the `tomcat_java_home` variable.

Role Variables
--------------

`tomcat_java_home` The path to your java installation. This variable is required in the systemd service file.

Dependencies
------------

A running Java installation like open-jdk-8.

Installation of the Role
----------------

`ansible-galaxy install FlxPeter.tomcat8`

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: FlxPeters.tomcat8, tomcat_java_home: /path/to/java/jre }

For assistance on getting location of java_home from your server check stackoverflow answer [here](https://stackoverflow.com/a/23427862/5128251)

Test
----

This roles uses Molecule to test. You can run the tests like this:

    molecule test

License
-------

MIT / BSD
