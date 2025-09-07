# "Система мониторинга "Zabbix" - "Рыхлик Илья"' 

---

### Задание 1

Установите Zabbix Server с веб-интерфейсом.

** Процесс выполнения **
1. Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
2. Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
3. Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
4. Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.
** Требования к результатам **
1. Прикрепите в файл README.md скриншот авторизации в админке.
2. Приложите в файл README.md текст использованных команд в GitHub.

---

### Решение 1

скриншот авторизации в админке Zabbix
![Авторизация Zabbix](https://github.com/ilaryhlik17854-stack/8-03-hw/blob/main/img/Zabbiz_auth.png?raw=true)

`Команды для установки Zabbix`
```
apt install postgresql
заходим на сайт https://www.zabbix.com/download и под нашу систему формируем набор команд
![Установка Zabbix](https://github.com/ilaryhlik17854-stack/8-03-hw/blob/main/img/Agent_download.png?raw=true)
wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_6.0+debian11_all.deb
dpkg -i zabbix-release_latest_6.0+debian11_all.deb
apt update
apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
DBPassword=123345678
![Пароль для базы Zabbix](https://github.com/ilaryhlik17854-stack/8-03-hw/blob/main/img/DBPassword.png?raw=true)
systemctl restart zabbix-server zabbix-agent apache2
systemctl enable zabbix-server zabbix-agent apache2
Даллее через браузер настроиваем Zabbix http://"192.168.100.89"/zabbix
```


---

### Задание 2

Установите Zabbix Agent на два хоста.

**Процесс выполнения**
1. Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
2. Установите Zabbix Agent на 2 вирт.машины, одной из них может быть ваш Zabbix Server.
3. Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов.
4. Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera.
5. Проверьте, что в разделе Latest Data начали появляться данные с добавленных агентов.

**Требования к результатам**
1. Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
2. Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
3. Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
4. Приложите в файл README.md текст использованных команд в GitHub

---

### Решение 2

1. Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
Мы подключили два хоста с Zabbix Agent установленного на Debian 11 и 12
![Hosts Zabbix](https://github.com/ilaryhlik17854-stack/8-03-hw/blob/main/img/Zabbix_hosts.png?raw=true)

2. Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
Hosts Debian11
![Debian11 Log](https://github.com/ilaryhlik17854-stack/8-03-hw/blob/main/img/debian11.png?raw=true)
Hosts Debian11
![Debian12 Log](https://github.com/ilaryhlik17854-stack/8-03-hw/blob/main/img/debian12.png?raw=true)

3. Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.

![Lasted data Zabbix](https://github.com/ilaryhlik17854-stack/8-03-hw/blob/main/img/LastedDate.png?raw=true)

4. Приложите в файл README.md текст использованных команд в GitHub
![agent download Zabbix](https://github.com/ilaryhlik17854-stack/8-03-hw/blob/main/img/Agent_download.png?raw=true)
wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_6.0+debian11_all.deb
dpkg -i zabbix-release_latest_6.0+debian11_all.deb
apt update
apt install zabbix-agent
systemctl restart zabbix-agent
systemctl enable zabbix-agent

### Задание 3*

Установите Zabbix Agent на Windows (компьютер) и подключите его к серверу Zabbix.

**Требования к результатам**
1. Приложите в файл README.md скриншот раздела Latest Data, где видно свободное место на диске C:

---

### Решение 3*

Не смог в опрошенных Templates найти параметр по опросу диска С:
Прикрепляю те данные которые смог опрость
![Windosw_Host_Zabbix](https://github.com/ilaryhlik17854-stack/8-03-hw/blob/main/img/Windosw_Host.png?raw=true)

![Windosw_Templates_Zabbix](https://github.com/ilaryhlik17854-stack/8-03-hw/blob/main/img/Windosw_Templates.png?raw=true)

