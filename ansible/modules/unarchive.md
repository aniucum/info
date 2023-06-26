```
- name: Unarchive a node_exporter.tar
  ansible.builtin.unarchive:
    src: https://github.com/prometheus/node_exporter/releases/download/v1.3.1/node_exporter-1.3.1.linux-amd64.tar.gz
    dest: /usr/local/bin
    remote_src: yes
    extra_opts:
    - --transform
    - s/^node_exporter-.*/node_exporter/
```
Without `--strip-components=1` archive alertmanager-0.25.0.linux-amd64.tar.gz will extract in /usr/local/bin/alertmanager-0.25.0.linux-amd64, with `--strip-components=1` will extract in /usr/local/bin/
```
- name: Extract alertmanager-0.25.0.linux-amd64.tar.gz
  ansible.builtin.unarchive:
    src: "https://github.com/prometheus/alertmanager/releases/download/v0.25.0/alertmanager-0.25.0.linux-amd64.tar.gz"
    dest: "/usr/local/bin/"
    remote_src: yes
    group: prometheus
    owner: prometheus
    mode: 0755
    extra_opts:
    - --strip-components=1    
    exclude:
    - alertmanager.yml
    - LICENSE
    - NOTICE
```