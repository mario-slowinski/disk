disk
====

Ansible role to manage:

* [disk partitions](https://docs.ansible.com/ansible/latest/collections/community/general/parted_module.html)
* [LVM volume groups](https://docs.ansible.com/ansible/latest/collections/community/general/lvg_module.html)
* [LVM volumes](https://docs.ansible.com/ansible/latest/collections/community/general/lvol_module.html)
* [filesystem](https://docs.ansible.com/ansible/latest/collections/community/general/filesystem_module.html)
* [mounts](https://docs.ansible.com/ansible/latest/collections/ansible/posix/mount_module.html)

Requirements
------------

* [ansible.builtin](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/index.html)
* [ansible.posix](https://docs.ansible.com/ansible/latest/collections/ansible/posix/index.html)
* [community.general](https://docs.ansible.com/ansible/latest/collections/community/general/)

Role Variables
--------------

* defaults

  ```yaml
  disk_partitions: []   # list of disk partitions to manage

  disk_vgs: []          # list of LVM volume groups to manage
      pvs: []           # list of PVS for VG

  disk_lvols: []        # list of LVM volumes to manage

  disk_filesystems: []  # list of LVM volumes to manage
    opts: []            # list of options passed to mkfs

  disk_mounts: []       # list of mounts to manage
    opts: []            # list of options passed to mount
  ```

Dependencies
------------

There are no dependencies.

Example Playbook
----------------

* `requirements.yml`

  ```yaml
  - name: disk
    src: https://github.com/mario-slowinski/disk
  ```

* playbook usage

  ```yaml
  - hosts: servers
    gather_facts: false
    roles:
      - role: disk
        tasks_from: mount.yml 
        # manage only mounts, same effect if only disk_mounts is defined
  ```

License
-------

[GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.html)

Author Information
------------------

[mario.slowinski@gmail.com](mailto:mario.slowinski@gmail.com)
