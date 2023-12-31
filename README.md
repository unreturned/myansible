Начальная настройка.

Ставим пакеты
```
ansible -vv --inventory inventory.ini basic --user root --ask-pass --module-name raw --args "apk update; apk upgrade -a; apk add python3 sudo"
ansible -vv --inventory inventory.ini basic --user root --ask-pass --module-name raw --args "echo '%wheel ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/mysudoers"
ansible -vv --inventory inventory.ini basic --user root --ask-pass --module-name raw --args "adduser dkovalkov"
ansible -vv --inventory inventory.ini basic --user root --ask-pass --module-name raw --args "adduser dkovalkov wheel"
```

```
ansible -vv --inventory inventory.ini basic --user dkovalkov --ask-pass -m command --args 'cat /etc/os-release'
```

Для того, чтобы стартовать плейбук, выполни, пожалуйста

```
ansible-playbook --verbose --inventory inventory.ini mydocker.yaml --check
```

```
ansible --inventory inventory.ini all -m ping
```

Обновление

```
ansible -vv --inventory inventory.ini basic --user dkovalkov --ask-pass --become --module-name raw --args "apk update; apk upgrade -a"
ansible -vv --inventory inventory.ini basic --user dkovalkov --become --module-name raw --args "apk update; apk upgrade -a"
```
