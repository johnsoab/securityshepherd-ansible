Role Name
=========

This role will provision your VM to become an OWASP Security Shepherd server for CTF / InfoSec training purposes.
It installs mariadb, tomcat, and firewalld.
It will modify firewalld to map 80->8080, and 443->8443, as well as allow all four ports inbound (future may drop 8080 and 8443 from public zone, not needed).
It will install a custom tomcat/mysql selinux policy which allows tomcat to talk to mysql ports over the network.
It will install a modified core and module schemas from OWASP SecurityShepherd, as well as the webapp v3.01
Future state will pick up from OWASP Project repo, for now, baked in to role.


Requirements
------------

RedHat or CentOS 7 is the only prequisite at this time.
Tested with CentOS 7.4

Role Variables
--------------

Check all values of defaults/main.yml, and copy to vars/main.yml as desired.. Highly recommend changing securityshepherd_admin_pass at a minimum.
Currently, mysql_root_pass will not work right, as webapp properties file needs to be modified. Will add in future.

If you set ss_reset_core_database: false -- it will NOT wipe out the core database (which contains all your players and scores). Default is TRUE
If you set ss_reset_module_database: false -- it will NOT wipe out the game module database, which contains level info. Default is TRUE. This is generally safe to leave, and sometimes required.


Dependencies
------------

None currently.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

MIT

Author Information
------------------

Andy Johnson (andyjohnsonfl@gmail.com)
