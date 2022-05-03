# Ansible role - Iptables

This role sets iptable rules and makes them persistent.

## Requirements

* This role requires root access, so you either need to specify `become` directive as a global or while invoking the role.

    ```yml
    become: yes
    ```

* Also requires Ansible variables, therefore do not disable directive `gather_facts`.

## Role paramaters

Optional parameters.

* `iptables_rules` - The list of **iptables** modules. For more information read Ansible documentation for module [iptables](https://docs.ansible.com/ansible/latest/modules/iptables_module.html).

## Example

Example that sets simple nat.

```yml
roles:
    - role: iptables
      iptables_rules:
          - table: nat
            chain: POSTROUTING
            out_interface: eth0
            jump: MASQUERADE
```
