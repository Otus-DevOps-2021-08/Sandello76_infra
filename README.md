# Sandello76_infra
Sandello76 Infra repository

- подключение к хосту при помощи ssh тунеля осуществлено через конфигурацию .ssh/config :

 Host bastion \
     HostName 84.252.129.79 \
     User appuser \
     Port 22 \
     IdentityFile ~/.ssh/appuser 


 Host someinternalhost \
     HostName 10.128.0.30 \
     User appuser \
     Port 22 \
     IdentityFile ~/.ssh/appuser \
     ProxyCommand  ssh appuser@bastion nc %h %p 
- подключение по команде someinternalhost реализовано по добавленному алиасу в ~/.bashrc

alias someinternalhost='ssh someinternalhost'


bastion_IP = 84.252.129.79
 
someinternalhost_IP = 10.128.0.30

testapp_IP = 62.84.113.176

testapp_port = 9292


- Доп задание:

доступ к админ панели организован по https://84-252-129-79.sslip.io

- Доп задание урок 6:

yc compute instance create \
  --name reddit-app \
  --hostname reddit-app \
  --memory=4 \
  --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1604-lts,size=10GB \
  --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4 \
  --metadata serial-port-enable=1 \
  --metadata-from-file user-data=./startup.yml


 - использовалось: https://cloudinit.readthedocs.io/en/latest/topics/examples.html
