

## Instalation

###### Install ansible to the control machine with commands:

```
  sudo apt-get install software-properties-common 
  sudo pip install ansible==2.8.0.0
```

###### Copy or symlink files `hosts` and `ssh_config`

```
  sudo ln -s $(pwd)/hosts /etc/ansible/hosts
```


### Run playbook:
For select hosts, use `-l` or `--limit` argument
For tag, use `-t` or `--tag` argument
Parameter: `-e 'ansible_python_interpreter=/usr/bin/python'` choose your interpreter running on host
Example:
```
ansible-playbook -v common.yml -l test1 -t example-tag -i hosts
```

##### If you don't make any changes, use`--check` argument:

  `ansible-playbook database.yml --limit slaves --check`

##### If you don't make any changes and you want to see every differences of possible changes use `--diff` argument:

  `ansible-playbook database.yml --limit slaves --check --diff`



### First server setup advice:
On the server setup your public ssh and install `python3-apt` 

then run:
ansible-playbook -v common.yml -t common -i /etc/ansible/hosts --limit ovh-vps --check
and
ansible-playbook -v common.yml -t docker -i /etc/ansible/hosts --limit ovh-vps --check

and if all is ok so then run it without --check

test if you can connect again with ssh and then reboot server

