# Ansible Role: ocstore_sync

Sync ocStore on Linux.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values:

ocstore_sync_dir: "resources/{{ inventory_hostname }}/sync"
ocstore_sync_tasks: []

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - Akman.ocstore_sync

*Inside `vars/main.yml`*:

ocstore_sync_dir: "resources/{{ inventory_hostname }}/sync"

ocstore_sync_tasks:
  - path: "{{ ocstore_shared_dir }}/image/data/avatars/300"
    mode: "pull"
    options:
      - "--delete-before"
  - path: "{{ ocstore_shared_dir }}/download"
    mode: "push"
    options:
      - "--delete-after"
      - "--exclude=index.html"
  - path: "{{ ocstore_shared_dir }}/image"
    mode: "push"
    options:
      - "--delete-after"
      - "--exclude=/cache/"
      - "--exclude=/no_image.jpg"
      - "--exclude=index.html"
  - path: "{{ ocstore_shared_dir }}/css"
    mode: "push"
    options:
      - "--delete-after"
      - "--exclude=index.html"

## License

MIT / BSD

## Author Information

This role was created in 2017 by Alexander Kapitman
