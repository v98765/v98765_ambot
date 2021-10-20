Role Name : Alertmanager bot
=========

Deploy and configure [alertmanager bot](https://github.com/metalmatze/alertmanager-bot)

Role Variables
--------------

Name | Default Value
---|---
`ambot_version` | "0.4.3"
`ambot_system_user` | "ambot"
`ambot_system_group` | "ambot"
`ambot_config_dir` | "/etc/ambot"
`ambot_db_dir` | "/var/lib/ambot"
`ambot_install_dir` | "/usr/local/bin"
`ambot_repo_dir` | "/var/tmp/archive"
`ambot_telegram_token` | "123456789:AABBCCdd"
`ambot_alertmanager_url` | "http://127.0.0.1:9093"
`ambot_listen_addr` | "127.0.0.1:8080"
`ambot_store` | "bolt"
`ambot_bolt_path` | "{{ ambot_db_dir }}/ambot.db"
`ambot_template_path` | "{{ ambot_config_dir }}/telegram.tmpl"

Files
-----

```sh
mkdir -p /var/tmp/archive
cd /var/tmp/archive
wget https://github.com/metalmatze/alertmanager-bot/releases/download/0.4.3/alertmanager-bot-0.4.3-linux-amd64
tar zcvf alertmanager-bot-0.4.3-linux-amd64.tar.gz alertmanager-bot-0.4.3-linux-amd64
```

Example Playbook
----------------

```yaml
---
- hosts: alerts
  gather_facts: true
  connection: ssh
  roles:
    - v98765_alertmanager
    - v98765_ambot
```
host_vars/alerts.yml
```yaml
ambot_telegram_admins:
  - 12
  - 34
ambot_telegram_token: "56"
```

License
-------

BSD
