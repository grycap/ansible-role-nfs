[![License](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![CI](https://github.com/grycap/ansible-role-nfs/workflows/CI/badge.svg)](https://github.com/grycap/ansible-role-nfs/actions?query=workflow%3ACI)

NFS server/client Role
=======================

Install NFS server/client (recipe for EC3).

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows.

	# Type of node to install: front or wn
	nfs_mode: front
	# Shared directories to export ( line to add to the /etc/exports file )
	nfs_exports: ""
	# Shared directories to mount
	nfs_client_imports: ""
	# Only enable NFSv4
	nfs_only_v4: false

Example Playbook
----------------
```
  - hosts: server
  roles:
  - { role: 'grycap.nfs', nfs_mode: 'front', nfs_exports: [{path: "/home", export: "vnode*.localdomain(fsid=0,rw,async,no_root_squash,no_subtree_check,insecure)"}] }
```
```
  - hosts: client
  roles:
  - { role: 'grycap.nfs', nfs_mode: 'wn', nfs_client_imports: [{ local: "/home", remote: "/home", server_host: "{{hostvars['server']['ansible_default_ipv4']}}" }] }
```

Contributing to the role
========================
In order to keep the code clean, pushing changes to the master branch has been disabled. If you want to contribute, you have to create a branch, upload your changes and then create a pull request.  
Thanks
