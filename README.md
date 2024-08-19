# Otus Homework 25. Web.
### Цель домашнего задания
Получить практические навыки в настройке инфраструктуры с помощью манифестов и конфигураций;
Отточить навыки использования ansible/vagrant/docker.
### Описание домашнего задания

Варианты стенда:

- nginx + php-fpm (laravel/wordpress) + python (flask/django) + js(react/angular);
- nginx + java (tomcat/jetty/netty) + go + ruby;
- можно свои комбинации.

Реализации на выбор:
- на хостовой системе через конфиги в /etc;
- деплой через docker-compose.
## Выполнение
Задание выполняется с помощью **Docker**. Установка:
```bash
sudo apt update
sudo apt install ca-certificates curl
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
```
Необходимо развернуть 5 docker контейнеров:
|Название|Образ|Порты|Зависимость|
|-|-|-|-|
|nginx|nginx:latest|8081:8081, 8082:8082, 8083:8083|worpdress, node, app|
|db|mysql:8.0|||
|wordpress|wordpress:6.6.1-fpm-alpine||db|
|node|node:16.13.2-alpine3.15|||
|app||||
