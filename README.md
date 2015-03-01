Ansible-Makepkg
===============

**ansible-makepkg** is a module for **[Ansible](https://github.com/ansible/ansible)** that encapsulates the process of building and installing a package from Arch Linux's AUR or from a custom source tarball. It is modelled on the process taken by the Aura package manager building as the user, installing as root and leaving a copy of the package in the local package cache (**/var/cache/pacman/pkg/**).

Usage
=====

Installing
----------

To use this module simply clone this repository into your library folder:

	$ cd library/
	$ git clone https://github.com/gunzy83/ansible-makepkg.git

Example Plays
-------------

	- name: Ensure aurvote is installed
	  makepkg:
	    name: aurvote
		state: present

	- name: Ensure custom-pkg is installed
	  makepkg:
	    name: /tmp/custom-pkg.src.tar.gz
	    state: present

	- name: Ensure aurvote is not installed (recursively remove dependencies)
	  makepkg:
	    name: aurvote
	    state: absent
	    recurse: true

	- name: Ensure aurvote is installed as a dependency of another package
	  makepkg:
	    name: aurvote
	    state: present
	    as_deps: true

	- name: Ensure aurvote is installed but built in a custom build directory
	  makepkg: 
	    name: aurvote
	    state: present
	    build_dir: "~/builds"

Future Plans
============

* Implement more options of makepkg and pacman (eg force)
* Submit to Ansible Extra Modules repository

License
=======

ansible-makepkg is provided under the same license as Ansible (GNU General Public License Version 3)

Copyright © 2015, Ross Williams