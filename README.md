sa-java
=========

[![Build Status](https://travis-ci.org/softasap/sa-java.svg?branch=master)](https://travis-ci.org/softasap/sa-java)
[![Includes support for Windows with PS5](https://img.shields.io/badge/Windows-Friendly-blue.svg)](https://img.shields.io/badge/Windows-Friendly-blue.svg)

Installs openjdk 7-8-11 controlled by java_package variable

Oracle java is no longer supported for installation.  You might consider amazon corretto distribution (sa-java-corretto role)

Usage example:

```YAML

     - {
         role: "sa-java"
       }

```

# Windows support

For windows support we expect, that box is prepared for provisioning with ansible (best used with role  https://github.com/softasap/sa-box-bootstrap-win ,
but if you configured the same setup manually will work too )

For windows systems there is only one parameter supported:  `java_version`

Example of the typical windows play:

```YAML

vars:
  - root_dir: ..

  - ansible_connection: winrm
  - ansible_ssh_port: 5986
  - ansible_winrm_server_cert_validation: ignore
  - ansible_winrm_transport: ssl


pre_tasks:
  - debug: msg="Pre tasks section"

  - name: gather facts
    setup:

roles:
   - {
       role: "sa-java",
       java_version: 8
     }

```

Notes
-----

List available java installations

`sudo  update-java-alternatives --list`

Switch default java

`sudo  update-java-alternatives --set [JDK/JRE name e.g. java-8-oracle]`

Magic oneliners to export JAVA_HOME

JRE:
`export JAVA_HOME=$(readlink -f /usr/bin/java | sed "s:bin/java::")`

JDK:

`export JAVA_HOME=$(readlink -f /usr/bin/java | sed "s:jre/bin/java::")`


If you want to use different JDKs/JREs for each Java task, you can run update-alternatives to configure one java executable at a time; you can run

`sudo  update-alternatives --config java[Tab]`
to see the Java commands that can be configured (java, javac, javah, javaws, etc). And then

`sudo  update-alternatives --config [javac|java|javadoc|etc.]`

Usage with ansible galaxy workflow
----------------------------------

If you installed the sa-java  role using the command


`
   ansible-galaxy install softasap.sa-java
`

the role will be available in the folder library/sa-java

Please adjust the path accordingly.

```YAML

     - {
         role: "softasap.sa-java"
       }

```



Copyright and license
---------------------

Code is dual licensed under the [BSD 3 clause] (https://opensource.org/licenses/BSD-3-Clause) and the [MIT License] (http://opensource.org/licenses/MIT). Choose the one that suits you best.

Reach us:

Subscribe for roles updates at [FB] (https://www.facebook.com/SoftAsap/)

Join gitter discussion channel at [Gitter](https://gitter.im/softasap)

Discover other roles at  http://www.softasap.com/roles/registry_generated.html

visit our blog at http://www.softasap.com/blog/archive.html
