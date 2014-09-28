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
- walrus | S3 builtin-backend
- cc | Cluster Controllers
- sc | Storage Controllers
- nc | Node Controllers

Role Variables
--------------

These variables are to be let by default as they point to the official packages repositories. Change only if you know what you are doing.

| Name | Has default ? | Description | Note
|--- |--- |--- |---
| euca_repo_url | Yes | Setup Eucalyptus cloud official repository package | RPM file
| euca2ools_repo_url | Yes | Setup euca2ools official repostory package | RPM file
| epel_repo_url | Yes | Setup EPEL official repository package | RPM file
| elrepo_repo_url | Yes | Setup EL-Repo official repository package | RPM File


These values define the private repos you are going to use. These are mandatory when setting **euca_use_local_repo** to *true*

| Name | Default | Description | Note
|--- |--- |--- |---
| euca_use_local_repo| false | If you have your own eucalyptus repository, set to true | None
| euca_local_repo_url | None | Specify the URL of your own Eucalyptus repository | Must be an URL
| euca2ools_local_repo_url | None | Specify the URL of your own euca2ools repository | Must be an URL


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
