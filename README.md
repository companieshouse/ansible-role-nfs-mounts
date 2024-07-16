# NFS role

An [Ansible Galaxy](https://galaxy.ansible.com/) role for configuring persistent NFS filesystem mounts.

## Table of contents

* [NFS Configuration][1]
* [Example Requirements File][2]
* [Example Playbook][3]
* [License][4]

[1]: #nfs-configuration
[2]: #example-requirements-file
[3]: #example-playbook
[4]: #license

## NFS Configuration

NFS filesystem mounts are configured using the `nfs_mounts_config` group/host variable. This variable should be defined as a list of dictionaries, each of which support the following parameters:

| Name          | Default             | Description                                                                           |
|---------------|---------------------|---------------------------------------------------------------------------------------|
| `path`        |                     | The path on the remote system being provisioned which will be used as the mount point for the NFS filesystem. |
| `src`         |                     | The source of the NFS filesystem in the form of the hostname or IP address of the NFS server and the directory being exported (e.g. `1.2.3.4:/exported`). |
| `opts`        | `hard,bg,nfsvers=4` | _Optional_. Options for the NFS filesystem that will be added to the filesystem table configuration (i.e. `/etc/fstab`) in the form of a single comma-separated string. |
| `symlink`     |                     | _Optional_. An optional path that will be used to create a symbolic link to the mount `path` specified. |

## Example Requirements File

```yml
- src: https://github.com/companieshouse/ansible-role-nfs-mounts
  name: nfs-mounts
  version: "n.n.n"
```

## Example Playbook

```yml
    - hosts: servers
      roles:
        - nfs-mounts
```

## License

This project is subject to the terms of the [MIT License](/LICENSE).
