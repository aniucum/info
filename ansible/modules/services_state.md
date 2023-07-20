
```
---
- name: collect facts about system services
  service_facts:
  register: services_state

- name: Debug
  debug:
    var: services_state.ansible_facts.services["firewalld.service"].state

- name: Add firewalld rules
  ansible.posix.firewalld:
    port: "{{ item }}"
    permanent: yes
    state: enabled
  loop:
    - 9100/http
  when: services_state.ansible_facts.services["firewalld.service"].state == running
  notify: reload firewalld
```