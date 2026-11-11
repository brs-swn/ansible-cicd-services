OKD Services
=========

This configures the following services required for deploying and operating
OKD4 (or OpenShift) and is tailored to a Libvirt/KVM deployment. The services
that are configured with this role are:

* Apache HTTPD
* ISC DHCP
* DNS/Bind
* HAProxy

Requirements
------------

This Role is customized for Fedora Linux 41 or higher. Other distributions
can be used, but updates to packaging and paths would have to be changed.
This assumes that a basic OS is installed with the proper partitions to 
accommodate the minimum storage. Hosts file, user accounts and NTP are also 
assumed to be configured.

The tested hardware for this role is:
  - Raspberry Pi 5
  - Storage: SD ED2S5 128 Gb Flash

Role Variables
--------------

See the default variable list for variables that can be overriden in the inventory group vars.

Also, host names, IP and MAC addresses are defined in the inventory hosts. See the example hosts file.

Dependencies
------------

 - An ansible user with SSH keys must already be configured on the target host.
 - It is advisable to to configure NTP.
 - No other Galaxy roles should be necessary to use this role.

Example Playbook
----------------
The play book should be defined as follows:

    - hosts: okd_services
      become: yes
      become_user: root
      roles:
        - ansible-okd-services

To execute the playbook use the following syntax:

    export ANSIBLE_CONFIG=ansible.cfg

    ansible-playbook \
     --private-key ~/.ssh/ansible-id_rsa \
     -u ansible \
     -i ../inventory/hosts \
     services-playbook.yml

License
-------

GPL-2.0-or-later

Author Information
------------------

Brent R. Scott <brs.scottworks@gmail.com>
