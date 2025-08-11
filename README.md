# ansible-study
## Handlers - 
### Handlers in Ansible are special tasks that run only when notified.They're usually used for things like restarting a service after a config file has changed.Think of them like ‘event-driven’ tasks. If something changes, then the handler is triggered — if not, it's skipped. This helps avoid unnecessary restarts or reconfigurations.


### Handlers in Ansible are like conditional tasks — they only run when something changes. For example, I have an EC2 instance running the Apache httpd server. If I update the httpd config file using Ansible, I only want to restart the httpd service if the config file actually changed. So I define a handler called 'restart httpd', and the task that updates the config file will notify it only if something was modified.

### ---
- name: Example Playbook with httpd and handler
  hosts: webserver
  become: yes

  tasks:
    - name: Update httpd config file
      copy:
        src: httpd.conf
        dest: /etc/httpd/conf/httpd.conf
      notify: Restart httpd

  handlers:
    - name: Restart httpd
      service:
        name: httpd
        state: restarted





### Handlers are defined under the handlers section.

### They are triggered using notify.

### If the task reports "changed", the handler runs at the end of the playbook.

### This makes the playbook idempotent — which means I can run it multiple times, and it only makes changes when needed. It’s efficient and avoids unnecessary service restarts.
