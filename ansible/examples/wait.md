```
---
- hosts: localhost
  vars:
    local__service: ssh
  tasks:
    - block:
      - name: "Stop {{ local__service }} service"
        systemd:
          service: "{{ local__service }}"
          state: stopped

      - name: "Populate ansible_facts.services variable"
        ansible.builtin.service_facts:

      - name: "{{ local__service }} state will be stopped as expected"
        assert:
          that:
            ansible_facts.services[local__service].state == 'stopped'

      - name: "Start {{ local__service }} service"
        systemd:
          service: "{{ local__service }}"
          state: started

      - name: "Registered {{ local__service }} state will still be stopped as it was not refreshed"
        assert:
          that:
            ansible_facts.services[local__service].state == 'stopped'

      - name: "Refresh ansible_facts.services variable"
        ansible.builtin.service_facts:

      - name: "{{ local__service }} state will be running as expected"
        assert:
          that:
            ansible_facts.services[local__service].state == 'running'


    - block:
      - name: "Stop {{ local__service }} service"
        systemd:
          service: "{{ local__service }}"
          state: stopped

      - name: "Wait until {{ local__service }} service is stopped"
        ansible.builtin.service_facts:
        register: temp__service_facts
        until: temp__service_facts.ansible_facts.services[local__service].state == 'stopped'
        retries: 20
        delay: 2

      - name: "Start {{ local__service }} service"
        systemd:
          service: "{{ local__service }}"
          state: started

      - name: "Wait until {{ local__service }} service is running"
        ansible.builtin.service_facts:
        register: temp__service_facts
        until: temp__service_facts.ansible_facts.services[local__service].state == 'running'
        retries: 20
        delay: 2
```