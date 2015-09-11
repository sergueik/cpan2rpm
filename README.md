Info
----
Copy of the [cpan2rpm](http://search.cpan.org/dist/cpan2rpm/cpan2rpm) utility for generation of enterprise RPM repository for Perl modules which are too demanding to build at provisioning time. The project appears stale, script needs minor modifications.

Example
-------
Replace the Time::Hires with the latest CPAN version:
```
# perl -MCPAN -eshell
cpan[]> install Time::Hires
# find ~/.cpan/source -iname '*Time-Hires*' -exec cp {} ~rpmbuilder \;
# chown rpmbuilder:rpmbuilder ~rpmbuilder/*gz
# yum -y install perl
# rpm -q perl-Time-HiRes
# perl-Time-HiRes-1.9721-141.el6.x86_64
# adduser rpmbuilder -p <password>
# su - rpmbuilder
$ ./cpan2rpm  --mk-rpm-dirs=/tmp/test
$ ./cpan2rpm  Time-HiRes-1.9726.tar.gz 
$ cp /tmp/test/RPMS/perl-Time-HiRes-1.9726-1.x86_64.rpm .
$ exit
# rmp -ef perl-Time-HiRes-1.9721-141.el6.x86_64 --nodeps
# rmp -Uvv ~rpmbuilder/perl-Time-HiRes-1.9726-1.x86_64.rpm
# rpm -q perl-Time-HiRes
# perl-Time-HiRes-1.9726-1.x86_64
# yum -y reinstall perl 
  Warning: RPMDB altered outside of yum
# rm -fr /tmp/test/{BUILD,BUILDROOT,RPMS,SOURCES,SPECS,SRPMS}/*
# perl -MCPAN -e 'install XML::Parser'
# 
```
Prerequisites
-------------
`rpmdevtools`, `rpm-build`. Also need to install CPAM module interactively before
Successfully Converted Modules
------------------------------
  * Time::Hires
  * XML::XPath
  * XML::Parser (without listing expat-devel as package dependency) 


See Also
--------
  - [rpmbuild](https://github.com/jeekl/rpmbuild) chef cookbook.
  - [pupper-rpmbuild](https://github.com/dgutierrez1287/puppet-rpmbuild)

Author
------
[Serguei Kouzmine](kouzmine_serguei@yahoo.com)
