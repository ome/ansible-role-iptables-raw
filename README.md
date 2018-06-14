Iptables Raw
============

Import the Iptables Raw library and make it available as a task.

See these links for full documentation:
- https://nordeus.com/blog/engineering/managing-iptables-with-ansible-the-easy-way/
- https://github.com/Nordeus/ansible_iptables_raw
- https://github.com/ansible/ansible/pull/21054


Development
-----------
The [`library/iptables_raw.py`](library/iptables_raw.py) version is https://github.com/Nordeus/ansible_iptables_raw/tree/34672590224f393016ad086f82054319108e67ad (2018-02-18).


Example Playbook
----------------

    - hosts: localhost
      roles:
        - role: iptables-raw

      tasks:
        # Block all incoming connections apart from ssh
        - iptables_raw:
            name: test_rules
            keep_unmanaged: no
            rules: |
              -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
              -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
              -A INPUT -j REJECT
              -A FORWARD -j REJECT
              -A OUTPUT -j ACCEPT
            state: present


Author Information
------------------

ome-devel@lists.openmicroscopy.org.uk
