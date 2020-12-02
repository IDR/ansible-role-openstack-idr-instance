# Changes in Version 3

## Breaking changes

- `idr_vm_extra_groups` is used to create a new openstack instance metadata property called `groups2` instead of being appended to `groups` to get around the 255 character limitation on property values.
  If you are reading this property in a dynamic Ansible inventory script you will need to append the values from `groups2` to the list of Ansible groups taken from `groups`.
