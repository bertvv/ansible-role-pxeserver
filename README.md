# Ansible role `pxeserver`

An Ansible role for setting up a PXE boot server.

- Install necessary packages
- Configure and start necessary services (TFTP, DHCP, NFS)
- Make installation images available to clients

This role will download the kernel(s) and initrd(s) that you want to boot, but the filesystem (that will be shared over NFS) is not set up automatically.

## Requirements

No specific requirements

## Role Variables

*TODO*

| Variable              | Default                        | Comment                                                              |
| :---                  | :---                           | :---                                                                 |
| `pxeserver_directory` | `pxelinux`                     | Subdirectory under TFTP root for PXE specific files                  |
| `pxeserver_images`    | []                             | List of dicts specifying PXEboot images to be served. See below. |
| `pxeserver_ip`        | `ansible_default_ipv4.address` | IP address of the PXE server                                         |

You can specify the boot images to be served with the variable `pxeserver_images`, a dict containing the keys listed below. Keys are *mandatory* unless specified.

| Key          | Value                                                                  |
| :---         | :---                                                                   |
| `name`       | A unique identifier for the image                                      |
| `default`    | When `true`, this image is chosen as the default. May be omitted. |
| `kernel_url` | URL where to download the kernel image.                                |
| `initrd_url` | URL where to download the initrd image.                                |
| `label`      | Label for the PXE boot menu entry of this image.                       |

## Dependencies

This role depends on:

- [bertvv.tftp](https://galaxy.ansible.com/list#/roles/3597)
- [bertvv.dhcp](https://galaxy.ansible.com/list#/roles/4859)

## Example Playbook

See the [test playbook](tests/test.yml)

## Testing

The `tests` directory contains tests for this role in the form of a Vagrant environment. You should install the dependent roles

```ShellSession
$ cd tests/
$ ansible-galaxy install -p roles bertvv.dhcp
$ ansible-galaxy install -p roles bertvv.tftp
$ vagrant up
```

The last command creates a new CentOS 7 VM and applies the playbook [`test.yml`](tests/test.yml). This should result in a working PXE server.

## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section. Pull requests are also very welcome. Preferably, create a topic branch and when submitting, squash your commits into one (with a descriptive message).

## License

BSD

## Further reading

- J. East, and D. Domingo (eds.), 2015. [Setting up a remote diskless system](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Storage_Administration_Guide/ch-disklesssystems.html). In *Red Hat 7 Storage Administration Guide*
- Petr Bokoč, et. al, 2015. [Preparing for a network installation](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Installation_Guide/chap-installation-server-setup.html). In *Red Hat 7 Installation Guide.

## Author Information

Bert Van Vreckem (bert.vanvreckem@gmail.com)

