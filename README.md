# Sandello76_infra
Sandello76 Infra repository

- подключение к хосту при помощи ssh тунеля осуществлено при помощи конфигурации .ssh/config :

- Host bastion
     HostName 84.252.129.79
     User appuser
     Port 22
     IdentityFile ~/.ssh/appuser


- Host someinternalhost
     HostName 10.128.0.30
     User appuser
     Port 22
     IdentityFile ~/.ssh/appuser
     ProxyCommand  ssh appuser@bastion nc %h %p
- подключение по команде someinternalhost реализовано по добавленному алиасу в ~/.bashrc

alias someinternalhost='ssh someinternalhost'
