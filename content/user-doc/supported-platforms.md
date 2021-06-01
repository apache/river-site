Title: Supported platforms
license: https://www.apache.org/licenses/LICENSE-2.0


### Supported platforms

#### Operating systems
OS | Remarks
---|-----
solaris |
ubuntu | 
windows |
freebsd | No recent information available: No up to date JDK available.
osx | No recent information available: [osx build server unavailable](http://mail-archives.apache.org/mod_mbox/www-builds/201111.mbox/%3CCAOJNCYcgMtCrHeE4+MbOcnBRPELaVryoR7+4YpzFr3kwkto0TQ@mail.gmail.com%3E)

#### Java runtime versions

Version | Remarks
--------|------
7 | 
6 | 
1.5 | river-qa does not compile
1.4 | not supported

Notes:

 * JERI KerberosServerEndpoint uses com.sun.* api
 * Phoenix implementation uses com.sun.* api

The com.sun.* packages are only available on Sun/Oracle based JDK's

####


#### Authentication subsystems

System | Remarks
-------|-------
Kerberos | Untested

#### Testing framework
Our current quality assurance (QA) framework only works with JDK6. 
