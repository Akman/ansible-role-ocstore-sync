# Ansible Role: ocstore-sync

Sync ocStore on Linux.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values:

ocstore_sync_dir: "sync/{{ inventory_hostname }}"

ocstore_sync_download:
  - path: "{{ ocstore_shared_dir }}/image/data/avatars/300"
    options:
      - "--delete-before"

ocstore_sync_upload:
  - path: "{{ ocstore_shared_dir }}/download"
    options:
      - "--delete-after"
      - "--exclude=index.html"
  - path: "{{ ocstore_shared_dir }}/image"
    options:
      - "--delete-after"
      - "--exclude=cache/"
      - "--exclude=.htaccess"
      - "--exclude=index.html"

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - Akman.ocstore-sync

*Inside `vars/main.yml`*:

ocstore_sync_dir: "sync/{{ inventory_hostname }}"

ocstore_sync_download:
  - path: "{{ ocstore_shared_dir }}/image/data/avatars/300"
    options:
      - "--delete-before"

ocstore_sync_upload:
  - path: "{{ ocstore_shared_dir }}/download"
    options:
      - "--delete-after"
      - "--exclude=index.html"
  - path: "{{ ocstore_shared_dir }}/image"
    options:
      - "--delete-after"
      - "--exclude=cache/"
      - "--exclude=.htaccess"
      - "--exclude=index.html"

## License

MIT / BSD

## Author Information

This role was created in 2017 by Alexander Kapitman
