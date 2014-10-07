Role Name
=========

Setup all packages to the hosts according to their component-role

** *WARNING !!!* **
*This role has to be used in the deployment of Eucalyptus cloud !*

Requirements
------------

hosts:

- clc | Cloud Controller

- ufs | User Facing Services

- cc | Cluster Controllers

- sc | Storage Controllers

- nc | Node Controllers

- walrus | S3 builtin-backend

Role Variables
--------------

These variables are to be let by default as they point to the official packages repositories. Change only if you know what you are doing.

| Parameter | Required | Default | Description
|--- |--- |--- |---
| euca_repo_url | Yes | [Eucalyptus latest](https://www.eucalyptus.com/docs/eucalyptus/4.0/#install-guide/installing_euca_release.html)  | Eucalyptus release repo RPM
| euca2ools_repo_url | Yes | [euca2ools latest](https://www.eucalyptus.com/docs/eucalyptus/4.0/#install-guide/installing_euca_release.html)  | euca2ools release repo RPM
| epel_repo_url | Yes | [Epel Latest](http://downloads.eucalyptus.com/software/eucalyptus/4.0/centos/6/x86_64/epel-release-6.noarch.rpm) | EPEL latest repo RPM
| elrepo_repo_url | Yes | [ELrepo latest](http://downloads.eucalyptus.com/software/eucalyptus/4.0/centos/6/x86_64/elrepo-release-6.noarch.rpm)   | ELrepo latest RPM


These values define the private repos you are going to use. These are mandatory when setting **euca_use_local_repo** to *true*

| Parameter | Required | Default | Note
|--- |--- |--- |---
| euca_use_local_repo | No | false | If you have your own eucalyptus repository, set to true
| euca_local_repo_url | No | None | Specify the URL of your own Eucalyptus repository
| euca2ools_local_repo_url | No | None | Specify the URL of your own euca2ools repository
| epel_replace | No | true | Defines if the epel repo is installed by the playbook
| elrepo_replace | No | true | Defines if the elrepo is installed by the playbook
| flush_yum | No | true | Defines if the yum cache should be flushed
| yum_behaviour | No | present | Defines how yum is going to seek for packages. Latest will allow upgrades to newest packages.
| gpg_check | No | true | Defines if yum must take GPGChecks in account

Dependencies
------------

None. Can arrive before or after JohnPreston.eucalyptus-network with no impact on the playbook.

Example Playbook
----------------

Here is an example of the role usage in an Eucalyptus cloud deployment

```

- hosts: all
  roles:
  - JohnPreston.eucalyptus-setup

```

```

- hosts: all
  roles:
  - JohnPreston.eucalyptus-setup
  vars:
  - euca_use_local_repo: true
  - euca_local_repo_url: http://myreposerver.lan/eucalyptus/centos/6/x86_64/
  - euca2ools_local_repo_url: http://myreposerver.lan/euca2ools/centos/6/x86_64/


```


License
-------

Apache

Author Information
------------------

John Mille [John Preston]
