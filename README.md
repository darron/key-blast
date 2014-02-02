key-blast
=============

Need to distribute a file quickly to a number of remote servers running ssh?

Here's a simple way to do it.

First - create your [Ansible Inventory file](http://docs.ansible.com/intro_inventory.html). Here's a quick example:

```
[nonfiction]
124.45.232.193
124.124.107.156
124.124.107.186
124.124.99.47
124.124.97.199
124.124.96.19
124.124.107.110
21.5.189.199
21.5.233.43
21.5.235.234
21.5.228.168
21.5.228.172
21.56.217.80
21.56.242.194
```

Then export an env var to their location: `export ANSIBLE_HOSTS=~/.ansible_hosts`. Now install Ansible: `brew install ansible`

After that - update the key-blast.yml file and run it - in this example I used the local file instead of the url:

```
pico key-blast.yml # Update the hosts, user and vars section.
ansible-playbook key-blast.yml
[] darron@~/Dropbox/src/key-blast: ansible-playbook key-blast.yml 

PLAY [nonfiction] ************************************************************* 

TASK: [key-blast | Install a url to a file.] ********************************** 
skipping: [124.45.232.193]
skipping: [124.124.107.186]
skipping: [124.124.107.156]
skipping: [124.124.96.19]
skipping: [124.124.97.199]
skipping: [124.124.99.47]
skipping: [124.124.107.110]
skipping: [21.5.189.199]
skipping: [21.5.235.234]
skipping: [21.5.233.43]
skipping: [21.5.228.168]
skipping: [21.56.217.80]
skipping: [21.56.242.194]
skipping: [21.5.228.172]

TASK: [key-blast | Install template to a file.] ******************************* 
changed: [124.124.107.156]
changed: [124.124.97.199]
changed: [124.45.232.193]
changed: [124.124.99.47]
changed: [124.124.107.186]
changed: [124.124.107.110]
changed: [124.124.96.19]
changed: [21.5.189.199]
changed: [21.5.233.43]
changed: [21.5.235.234]
changed: [21.5.228.172]
changed: [21.5.228.168]
changed: [21.56.242.194]
changed: [21.56.217.80]

TASK: [key-blast | Set permissions on file.] ********************************** 
ok: [124.124.107.186]
ok: [124.45.232.193]
ok: [124.124.97.199]
ok: [124.124.99.47]
ok: [124.124.107.156]
ok: [124.124.107.110]
ok: [21.5.189.199]
ok: [124.124.96.19]
ok: [21.5.235.234]
ok: [21.5.233.43]
ok: [21.5.228.168]
ok: [21.5.228.172]
ok: [21.56.217.80]
ok: [21.56.242.194]

PLAY RECAP ******************************************************************** 
124.124.107.110            : ok=2    changed=1    unreachable=0    failed=0   
124.124.107.156            : ok=2    changed=1    unreachable=0    failed=0   
124.124.107.186            : ok=2    changed=1    unreachable=0    failed=0   
124.124.96.19              : ok=2    changed=1    unreachable=0    failed=0   
124.124.97.199             : ok=2    changed=1    unreachable=0    failed=0   
124.124.99.47              : ok=2    changed=1    unreachable=0    failed=0   
124.45.232.193             : ok=2    changed=1    unreachable=0    failed=0   
21.56.217.80               : ok=2    changed=1    unreachable=0    failed=0   
21.56.242.194              : ok=2    changed=1    unreachable=0    failed=0   
21.5.189.199              : ok=2    changed=1    unreachable=0    failed=0   
21.5.228.168              : ok=2    changed=1    unreachable=0    failed=0   
21.5.228.172              : ok=2    changed=1    unreachable=0    failed=0   
21.5.233.43               : ok=2    changed=1    unreachable=0    failed=0   
21.5.235.234              : ok=2    changed=1    unreachable=0    failed=0   
```

And now you're done.

Pretty handy in a pinch.