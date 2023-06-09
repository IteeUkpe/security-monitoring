Ansible NGINX Security Monitoring Role
=========

This ansible role helps in installing NGINX Management Suite Security Monitoring Module on the Management Plane.
You can use Security Monitoring Module to monitor NGINX App Protect WAF. The module provides analytics dashboards and security log details that provide protection insights and help you analyze possible threats or identify opportunities for tuning your security policies.

NGINX Management Suite Security Monitoring supports the following use cases:

Security Monitoring only: Use only the Security Monitoring module to monitor data from NGINX App Protect WAF instances. You will be able to review the security dashboards to assess potential threats and identify opportunities to fine-tune your policies. Your NGINX App Protect WAF configurations are managed outside of the NGINX Management Suite context.

Security Monitoring and Instance Manager: Use the Security Monitoring module with the NGINX Management Suite Instance Manager module. In addition to monitoring your application security, you will be able to manage your NGINX App Protect WAF configurations and security policies in a single location and push pre-compiled updates to an instance or instance group.

Requirements
------------
1. NGINX Management Suite License Files
2. NGINX Ansible Role (nginxinc.nginx)
3. Ansible Role NGINX Management Suite (nginxinc.nginx)
4. NGINX App Protect WAF

NGINX Management Suite Certificate Files
------------
Installing NMS requires the NMS certificate files to access the repository. Log in to MyF5 or follow the link in the trial activation email to download the NMS repo .crt and .key files:

- nginx-mgmt-suite-trial.key
- nginx-mgmt-suite-trial.crt

- NOTE: Be sure to rename these files to nginx-repo.key and nginx-repo.crt, respectively.

NGINX Instance
---------------
NMS requires an NGINX instance, either NGINX OSS or NGINX Plus as a frontend only. This role handles this by defining a dependency to the NGINX Ansible Role, named nginxinc.nginx. Because of this dependance, you can set variables related to nginxinc.nginx when using this role. For example, nginx_type is an nginxinc.nginx variable that can be set like how you would any other Ansible variable. So if your playbook defines nginx_type: plus, this NMS role will call the nginxinc.nginx role which will install NGINX Plus. Refer to the Ansible Role NGINX for more details.

Main difference between using NGINX OSS or NGINX Plus depends on which Authentication Option you plan to use.

Ansible
--------
This role is developed and tested with maintained versions of Ansible core (above 2.12).

This role was developed and tested using nginxinc.nginx version 0.24.0.

When using this role, you will also need to install the following collections below. Additional information installing these collections is below in the Installation section.

ansible.posix
community.general
community.crypto
community.docker (Only required if you plan to use Molecule)
You will need to run this role as a root user using Ansible's become parameter. Make sure you have set up the appropriate permissions on your target hosts.

Instructions on how to install Ansible can be found in the Ansible website.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------
travis.yml
```
---
- name: Install NGINX 
  hosts: nms_server
  become: true
  ignore_errors: true
  roles:
    - security_monitoring
```
To run the playbook:
```
ansible-playbook travis.yml
```
Author Information
------------------

Itoro Ukpe
© F5, Inc. 2023

