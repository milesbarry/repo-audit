# repo-audit

Is a Python script to group YUM repository information from a collection of
hosts and output a JSON structure of their repo names, urls, and IP's.

Full information can be found by executing it with --help.

It requires a source directory structure that contains a sub directory name
of the IP address(s) of the host(s). Within the IP directory you then have the
YUM repo file(s) that the host has. Eg: Our source directory is "yum-repos"
```sh
yum-repos
├── 100.78.254.2
│   ├── redhat.repo
│   ├── rhel-source.repo
│   └── yum.conf
├── 192.168.10.10
│   ├── cirb-centos.repo
│   ├── cirb.repo
│   └── yum.conf
├── 192.168.10.13
│   ├── nginx.repo
│   ├── nodesource-el.repo
│   ├── pgdg-94-redhat.repo
│   ├── redhat.repo
│   ├── snow.repo
│   └── yum.conf
```
Normally you will gather this using Ansible from all your hosts.
When using full output, you will see for example:
```json
{
    "Advance_Toolchain": {
        "baseurl:ftp://ftp.unicamp.br/pub/linuxpatch/toolchain/at/redhat/RHEL6": [
            [
                "192.168.13.27",
                "ibm-power-repo.repo"
            ],
            [
                "192.168.14.120",
                "ibm-power-repo.repo"
            ],
            [
                "192.168.14.231",
                "ibm-power-repo.repo"
            ],
            [
                "192.168.14.232",
                "ibm-power-repo.repo"
            ],
            [
                "192.168.24.201",
                "ibm-power-repo.repo"
            ],
        ]
    },
    "CIRB": {
        "baseurl:http://192.168.20.3/cirb/": [
            [
                "192.168.13.41",
                "cirb.repo"
            ],
            [
                "192.168.13.58",
                "cirb.repo"
            ]
        ]
    },
```
