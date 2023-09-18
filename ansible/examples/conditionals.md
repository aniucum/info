### https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_conditionals.html

- defined https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_conditionals.html#conditionals-based-on-variables
```
tasks:
    - name: Run the command if "foo" is defined
      ansible.builtin.shell: echo "I've got '{{ foo }}' and am not afraid to use it!"
      when: foo is defined

    - name: Fail if "bar" is undefined
      ansible.builtin.fail: msg="Bailing out. This play requires 'bar'"
      when: bar is undefined
```