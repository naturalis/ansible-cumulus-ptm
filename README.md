# Ansible Role: Cumulus ptm

Used in [network](https://github.com/naturalis/network/) repo.

Runnable with:
```bash
ansible-playbook playbooks/cumulus_ptm.yml -i environments/prod
```

This role will configure the ptm daemon and fill in the .dot file for topology checks.

## Requirements

None.

## Role Variables

Available variables are listed below:
```bash
check_ptm: true
check_lldp: true

ptm:
  - '"netdw2-spine-a":"swp47" -- "uplink01":"swp1"'
  - '"netdw2-spine-a":"swp48" -- "uplink02":"swp1"'
  - '"netdw2-spine-b":"swp47" -- "uplink01":"swp2"'
  - '"netdw2-spine-b":"swp48" -- "uplink02":"swp2"'
  - '"netdw2-spine-a":"swp49" -- "netdw2-spine-b":"swp49"'
  - '"netdw2-spine-a":"swp50" -- "netdw2-spine-b":"swp50"'
  - '"netdw2-spine-a":"swp1" -- "netdw2-leaf-d1a":"swp52"'
  - '"netdw2-spine-b":"swp1" -- "netdw2-leaf-d1d":"swp52"'
  - '"netdw2-spine-a":"swp2" -- "netdw2-leaf-h1a":"swp52"'
  - '"netdw2-spine-b":"swp2" -- "netdw2-leaf-h1d":"swp52"'
  - '"netdw2-leaf-d1a":"swp50" -- "netdw2-leaf-d1d":"swp50"'
  - '"netdw2-leaf-d1a":"swp49" -- "netdw2-leaf-d1b":"swp49"'
  - '"netdw2-leaf-d1d":"swp49" -- "netdw2-leaf-d1c":"swp49"'
  - '"netdw2-leaf-d1b":"swp50" -- "netdw2-leaf-d1c":"swp50"'
  - '"netdw2-leaf-d1b":"swp1" -- "host01":"swp1"'
  - '"netdw2-leaf-d1c":"swp1" -- "host02":"swp1"'
  - '"netdw2-leaf-h1a":"swp50" -- "netdw2-leaf-h1d":"swp50"'
  - '"netdw2-leaf-h1a":"swp49" -- "netdw2-leaf-h1b":"swp49"'
  - '"netdw2-leaf-h1d":"swp49" -- "netdw2-leaf-h1c":"swp49"'
  - '"netdw2-leaf-h1b":"swp50" -- "netdw2-leaf-h1c":"swp50"'
  - '"netdw2-leaf-h1b":"swp1" -- "host03":"swp1"'
  - '"netdw2-leaf-h1c":"swp1" -- "host04":"swp1"'
```

## Dependencies

None.

## Example Playbook


    - hosts: switches
      remote_user: cumulus
      vars:
        check_ptm: true
        check_lldp: true
      gather_facts: no
      become: true
      roles:
        - ansible-role-cumulus-common

## License

Apache2
