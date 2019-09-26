# OTUS ДЗ 9 Автоматизация администрирования. Ansible.  (Centos 7)
-----------------------------------------------------------------------
### Домашнее задание

    Подготовить стенд на Vagrant как минимум с одним сервером. На этом сервере используя Ansible необходимо развернуть nginx со следующими условиями:
    - необходимо использовать модуль yum/apt
    - конфигурационные файлы должны быть взяты из шаблона jinja2 с перемененными
    - после установки nginx должен быть в режиме enabled в systemd
    - должен быть использован notify для старта nginx после установки
    - сайт должен слушать на нестандартном порту - 8080, для этого использовать переменные в Ansible
    * Сделать все это с использованием Ansible роли

    Домашнее задание считается принятым, если:
    - предоставлен Vagrantfile и готовый playbook/роль ( инструкция по запуску стенда, если посчитаете необходимым )
    - после запуска стенда nginx доступен на порту 8080
    - при написании playbook/роли соблюдены перечисленные в задании условия
    Критерии оценки: Ставим 5 если создан playbook
    Ставим 6 если написана роль

Наша структура файлов и папок роли:
```
.
├── ansible.cfg
├── hosts
├── playbook
│   └── web.yml
├── Readme.md
├── roles
│   └── nginx
│       ├── defaults
│       │   └── main.yml
│       ├── files
│       ├── handlers
│       │   └── main.yml
│       ├── meta
│       │   └── main.yml
│       ├── README.md
│       ├── tasks
│       │   ├── main.yml
│       │   └── redhat.yml
│       ├── templates
│       │   ├── index.html.j2
│       │   └── nginx.conf.j2
│       ├── tests
│       │   ├── inventory
│       │   └── test.yml
│       └── vars
│           └── main.yml
└── vagrantfile
```

1. С помощью команды ```ansible-galaxy init roles/nginx``` создаем роль. Эта команда создаст нам структуру папок и файлов для работы.

2. Запуск производиться следующим образом ```ansible-playbook playbook/web.yml```. После запуска этого файла, вызывается файл ```/roles/nginx/tasks/mail.yml```.

3. Файл ansible.cfg должен лежать с vagrantfile в одной директории.