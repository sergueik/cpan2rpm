Info
----
Copy of the [cpan2rpm](http://search.cpan.org/dist/cpan2rpm/cpan2rpm) utility for generation of enterprise RPM repository for Perl modules which are toodemanding to build at provisioning time. The project appears stale, script needs minor modifications.

Example
-------
Replace the Time::Hires with the latest CPAN version:
```
# yum -y install perl
# rpm -q perl-Time-HiRes
# perl-Time-HiRes-1.9721-141.el6.x86_64
# assuser rpmuser
# su - rpmuser
$ ./cpan2rpm  --mk-rpm-dirs=/tmp/test
$ ./cpan2rpm  Time-HiRes-1.9726.tar.gz 
$ cp /tmp/test/RPMS/perl-Time-HiRes-1.9726-1.x86_64.rpm .
$ exit
# rmp -ef perl-Time-HiRes-1.9721-141.el6.x86_64 --nodeps
# rmp -Uvv perl-Time-HiRes-1.9726-1.x86_64.rpm
# rpm -q perl-Time-HiRes
# perl-Time-HiRes-1.9726-1.x86_64
```
See Also
--------
  - [rpmbuild](https://github.com/jeekl/rpmbuild) chef cookbook.
  - [pupper-rpmbuild](https://github.com/dgutierrez1287/puppet-rpmbuild)

Author
------
[Serguei Kouzmine](kouzmine_serguei@yahoo.com)
