Openstack IDR Instance
======================

Create an Openstack VM for use with the IDR playbooks.


Role Variables
--------------

Defaults: `defaults/main.yml`

Required variables:
- `idr_vm_name`: VM hostname
- `idr_vm_image`: Openstack base image
- `idr_vm_flavour`: Openstack flavour

Optional variables:
- `idr_environment`: Use this as a group prefix. This is required to ensure servers can lookup the address of other servers in the group, and is particularly important if multiple groups of servers are running in the same project. The default is `idr` but you should almost always set it to something else.
- `idr_vm_keyname`: Openstack SSH key, defaults to `idr-deployment-key` (see the `openstack-idr-keypairs` role)
- `idr_vm_private_networks`: Use this network instead of the default one
- `idr_vm_assign_floating_ip`: Assign a floating IP, default `False`
- `idr_vm_count`: Number of VMs to create, default `1` (named `idr_vm_name`).
   If `idr_vm_count > 1` then all instances will be named with a numeric suffix `idr_vm_name-N`
- `idr_vm_networks`: A list of `net-name: NETWORK_NAME` pairs

Booleans indicating the purpose of this server:
- If any of these are `True` they will be used to automatically set the security groups and host-groups for this VM, default `False`. Multiple may be set to `True` if a server has multiple purposes.
  - `idr_vm_database`: An IDR database server
  - `idr_vm_omeroreadwrite`: An IDR OMERO read-write server
  - `idr_vm_omeroreadonly`: An IDR OMERO read-only server
  - `idr_vm_proxy`: An IDR web proxy server
  - `idr_vm_dockermanager`: An IDR Docker server
  - `idr_vm_dockerworker`: An IDR Docker slave
  - `idr_vm_bastion`: An IDR gateway host with external SSH
  - `idr_vm_management`: An IDR monitoring server


Advanced settings:
- `idr_vm_groups`: A list of host-groups, default depends on the above booleans
- `idr_vm_extra_groups`: A list of host-groups in addition to the above default
- `idr_vm_security_groups`: A list of security groups, default depends on the above booleans


Development
-----------

See the warning in `tasks/main.yml` before making changes.


Author Information
------------------

ome-devel@lists.openmicroscopy.org.uk
