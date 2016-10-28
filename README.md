[![License](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![Build Status](https://travis-ci.org/grycap/ansible-role-nfs.svg?branch=master)](https://travis-ci.org/grycap/ansible-role-nfs)

NFS server/client Role 
=======================

Install NFS server/client.

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows.

	# NFS install mode: server or client
	nfs_mode: server
	# Line to add to the /etc/exports file
	nfs_exports: [{path: "/home", export: "vnode*(rw,async,no_root_squash,no_subtree_check,insecure)"}]
	# Line to add to the /etc/exports file
	nfs_client_imports: [{ local: "/home", remote: "/home", server_host: "{{hostvars['server']['ansible_default_ipv4']}}" }]

Example Playbook
----------------

This an example of how to install a Torque/PBS cluster:

    - hosts: server
      roles:
      - { role: 'grycap.nfs', nfs_mode: 'server', nfs_exports: [{path: "/home", export: "vnode*(fsid=0,rw,async,no_root_squash,no_subtree_check,insecure)"}] }

    - hosts: client
      roles:
      - { role: 'grycap.nfs', nfs_mode: 'client', nfs_client_imports: [{ local: "/home", remote: "/home", server_host: "{{hostvars['server']['ansible_default_ipv4']}}" }] }


Contributing to the role
========================
In order to keep the code clean, pushing changes to the master branch has been disabled. If you want to contribute, you have to create a branch, upload your changes and then create a pull request.  
Thanks

