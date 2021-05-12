AWS Corretto JDK
=========

This role downloads and installs an Aws Corretto JDK and sets it up as the default JDK on Ubuntu. The .deb files come from [AWS](https://docs.aws.amazon.com/corretto/).

[![Build Status](https://travis-ci.org/Rheinwerk/ansible-role-aws_jdk.svg?branch=master)](https://travis-ci.org/Rheinwerk/ansible-role-aws_jdk)

Requirements
------------

None.

Role Variables
--------------

None.

Dependencies
-----------

None.

Example Playbook
----------------

The general contract of this role is to take the variables map `_aws_jdk` from `defaults/main.yml` as a template for your configuration and pass that configuration as a parameter to this role.

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: aws_jdk, tags: [ 'jdk' ] }

License
-------

Please see LICENSE.

Author Information
------------------

Original author is [Jonathan Koch](https://github.com/devthat) as member of the [Rheinwerk](https://github.com/Rheinwerk) project.
