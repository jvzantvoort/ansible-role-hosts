# ansible-role-hosts

A role to maintain the ```/etc/hosts``` file

## Requirements

None

## Role Variables

| Name                 | Default            | Description |
| hosts_user           |  ```root```        | User of the file |
| hosts_group          |  ```root```        | group of the file |
| hosts_file           |  ```/etc/hosts```  | path of the file |
| add_inventory_host   |  ```false```       | add the local inventory entry to the hosts file |
| add_inventory_hosts  |  ```false```       | add all the entries to the hosts file |
| inventory_groups     |  ```[]```          | if ```add_inventory_hosts``` is true these groups will be used to add hosts to the hosts file |
| hosts_definitions    |  ```[]```          | seperate and uniq hosts entries |

# Dependencies

None

## Example Playbook

Add all hosts in the inventory to the hosts file:

    ---
    - hosts: all
      gather_facts: true
      tasks:
        - name:
          setup:
          become: true
    - hosts: localhost
      gather_facts: true
      tasks:
        - include_role:
            name: ansible-role-hosts
          vars:
            add_inventory_host: true
            add_inventory_hosts: true
            inventory_groups:
              - all
              - some
            hosts_definitions:
              - address: 192.168.1.105
                hostnames:
                  - m111
                  - m0a

## License

MIT

