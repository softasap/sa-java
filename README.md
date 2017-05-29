sa-java
=========

[![Build Status](https://travis-ci.org/softasap/sa-java.svg?branch=master)](https://travis-ci.org/softasap/sa-java)


Installs oracle java 7-8 controlled by java_version variable

java 8 is installed using rpm or oracle-java8-installer on debian.

Important update for oracle 7 on ubuntu, May 2017:
Oracle no longer provides public downloads, thus `oracle-java7-installer` no longer able to download distrubution.
As a workaround, role will install oracle java 7 from _source_ using some trusted by you mirror with files.

Please make sure, you trast mirror configured as `alternative_java_6_7_mirror`, also advise is to use your own mirror.

to make sure, you understand your responsibility, you need specifically set `true` to `option_accept_non_oracle_mirror`



```
# validate checksum against known to role one
option_validate_checksum: false  

# preferred mirror, if java download is not available
alternative_java_6_7_mirror: "ftp://ftp.slackware.com/.1/funtoo/distfiles/oracle-java/"

#settings for installation from sources
java_download_folder: /usr/src
java_folder: /usr/lib/jvm
java_alias: "java-{{java_version}}-oracle"

known_hashes:
  "jdk-7u80-linux-x64.tar.gz": "sha256:bad9a731639655118740bee119139c1ed019737ec802a630dd7ad7aab4309623"
```

Usage example:

```YAML

     - {
         role: "sa-java",
         java_version: 7
       }

```

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

Code licensed under the [BSD 3 clause] (https://opensource.org/licenses/BSD-3-Clause) or the [MIT License] (http://opensource.org/licenses/MIT).

Subscribe for roles updates at [FB] (https://www.facebook.com/SoftAsap/)
