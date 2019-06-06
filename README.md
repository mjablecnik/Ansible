

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
For selected hosts, use `-l` argument
For tag, use `-t` argument
Parameter: `-e 'ansible_python_interpreter=/usr/bin/python'` choose your interpreter running on host
```
ansible-playbook -v common.yml -l test1 -t example-tag -i hosts
```

##### Run playbook with `--check` argument for run playbook without changes:

  `ansible-playbook database.yml --check --limit slaves`


