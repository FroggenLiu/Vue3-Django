# vue

## install from packages
```
sudo apt install python3-django
sudo apt install python3-pip python3-venv
mkdir /home/froggenliu/pv && cd pv/
```

##create virtual environment
```
python3 -m venv pv
source pv/bin/activate
```

##config mysql allow remote access
```
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
#edit `bind-address`  to 0.0.0.0
bind-address            = 0.0.0.0
```

##restart service 
```
sudo systemctl restart mysql
```

##create database and user that can acess from anywhere(%)
'''
mysql -u root -p
CREATE DATABASE pcloudfw
CREATE USER 'froggenliu'@'%' IDENTIFIED BY 'password';
```

##grant permission for user on pcloud database
```
GRANT ALL on pcloudfw.* TO 'froggenliu'@'%';
FLUSH PRIVILEGES;
```


#below step are in virtual env

##create project
```
django-admin startproject provision
```

##create app
```
django-admin startapp login
```

##install mysqlclient
```
sudo apt-get install python3-dev default-libmysqlclient-dev build-essential
pip install mysqlclient
```

##install package
```
pip install djoser (a library for helping us authentication and tokens)
pip install django-rest-framework(a library for building the api)
pip install django-cors-headers(a library for handling the server headers Cross-origin resource sharing)
```

