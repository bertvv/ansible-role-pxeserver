# Ansible role `pxeserver`

An Ansible role for setting up a PXE boot server.

- Install necessary packages
- Configure and start necessary services (TFTP, DHCP, NFS)
- Make installation images available to clients

This role will download the kernel(s) and initrd(s) that you want to boot, but the filesystem (that will be shared over NFS) is not set up automatically.

**This role is unfinished and should only be used for testing.**

## Requirements

No specific requirements

## Role Variables


| Variable   | Required | Default | Comments (type)  |
| :---       | :---     | :---    | :---             |
| `role_var` | no       | -       | (scalar) PURPOSE |

## Dependencies

This role depends on:

- [bertvv.tftp](https://galaxy.ansible.com/list#/roles/3597)
- [bertvv.dhcp](https://galaxy.ansible.com/list#/roles/4859)

## Example Playbook

See the [test playbook](tests/test.yml)

## Testing

The `tests` directory contains tests for this role in the form of a Vagrant environment. The directory `tests/roles/pxeserver` is a symbolic link that should point to the root of this project in order to work. To create it, do

```ShellSession
$ cd tests/
$ mkdir roles
$ ln -frs ../../PROJECT_DIR roles/pxeserver
```

You may want to change the base box into one that you like. The current one is based on Box-Cutter's [CentOS Packer template](https://github.com/boxcutter/centos).

The playbook [`test.yml`](tests/test.yml) applies the role to a VM, setting role variables.

## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section. Pull requests are also very welcome. Preferably, create a topic branch and when submitting, squash your commits into one (with a descriptive message).

## License

BSD

## Further reading

- J. East, and D. Domingo (eds.), 2015. [Setting up a remote diskless system](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Storage_Administration_Guide/ch-disklesssystems.html). In *Red Hat 7 Storage Administration Guide*
- Petr Bokoč, et. al, 2015. [Preparing for a network installation](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Installation_Guide/chap-installation-server-setup.html). In *Red Hat 7 Installation Guide.

## Author Information

Bert Van Vreckem (bert.vanvreckem@gmail.com)

