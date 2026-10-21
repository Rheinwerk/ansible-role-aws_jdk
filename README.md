AWS Corretto JDK
=========

This role downloads and installs an Aws Corretto JDK and sets it up as the default JDK on Ubuntu. The .deb files come from [AWS](https://docs.aws.amazon.com/corretto/).

[![Build Status](https://github.com/Rheinwerk/ansible-role-aws_jdk/actions/workflows/ci.yml/badge.svg)](https://github.com/Rheinwerk/ansible-role-aws_jdk/actions/workflows/ci.yml)

Requirements
------------

None.

Role Variables
--------------

Every setting is one variable with a default in `defaults/main.yml`; set only the ones that differ.

| Variable | Default |
|---|---|
| `_aws_jdk_deb822_repository` | the Corretto apt repository (`https://apt.corretto.aws`, suite `stable`) as a list of deb822 entries |
| `_aws_jdk_package_name` | `java-21-amazon-corretto-jdk`; `<package>=<version>` pins a version, otherwise the latest is installed |
| `_aws_jdk_security` | `dns_cache_ttl: 30`, `dns_cache_negative_ttl: 0`, written as `networkaddress.cache.ttl` and `networkaddress.cache.negative.ttl` to `java.security` of every installed Corretto JDK |
| `_aws_jdk_cacerts_absent_aliases` | `comodoaaaca [jdk]`, `emsigneccrootcag3 [jdk]`, `emsigneccrootca-g3`: deleted with `keytool -delete` from `lib/security/cacerts` of every installed Corretto JDK, because these roots chain to the eMudhra intermediates with recoverable private keys ([October 2026](https://emudhra.we-have-a-problem.com/)) |

Until v0.5.0 the role took one `_aws_jdk` dict with the keys `deb822_repository`, `package_name`
and `security` instead.

Dependencies
-----------

None.

Example Playbook
----------------

Only the package differs from the defaults here:

    - hosts: servers
      vars:
        _aws_jdk_package_name: "java-17-amazon-corretto-jdk"
      roles:
         - { role: aws_jdk, tags: [ 'jdk' ] }

License
-------

Please see LICENSE.

Author Information
------------------

Original author is [Jonathan Koch](https://github.com/devthat) as member of the [Rheinwerk](https://github.com/Rheinwerk) project.
