# Blog Web Application base on Python-Flask framework



## Installation

- **Step 1**: clone the source code from GitHub
```
git clone https://github.com/JmilkFan/JmilkFan-s-Blog.git

cd JmilkFan-s-Blog
```

- **Step 2**: building and using virtual environment via tools of `virtualenv`
```
virtualenv blog_env

source blog_env/bin/activate
```

- **Step 3**: Install the requirements package
```
pip install -r requirements.txt -e .
```

## Start service

- **Srep 1**: Create the DB for app of jmilkfansblog, e.g.
```
mysql -uroot -pfanguiju -e "CREATE DATABASE myblog default charset utf8 COLLATE utf8_general_ci;"
mysql -uroot -pfanguiju -e "GRANT ALL ON egis.* TO 'user'@'127.0.0.1' IDENTIFIED BY 'fanguiju';"
mysql -uroot -pfanguiju -e "GRANT ALL ON egis.* TO 'user'@'localhost' IDENTIFIED BY 'fanguiju';"
mysql -uroot -pfanguiju -e "GRANT ALL ON egis.* TO 'user'@'%' IDENTIFIED BY 'fanguiju';"
```

- **Step 2**: Setup the Configuration.<br>
Edit the config option `connection` for etc file `etc/jmilkfansblog.conf` e.g.
```
connection = 'mysql+pymysql://root:fanguiju@127.0.0.1:3306/myblog?charset=utf8'
```

Edit the config option `host`/`server_port`/`api_port`. e.g.
```
host = '127.0.0.1'
server_port = 8089
api_port = 8080
```

- **Step 3**: Init the database
```
jmilkfansblog-manager db upgrade -d jmilkfansblog/db/sqlalchemy/alembic
```

- **Step 4**: Start the service
```
jmilkfansblog-manager server
```

- **Step 5**: Start the API service
```
jmilkfansblog-api
```

- **Step 6**: Register the account(Have to access the google reCAPTCHA).
```
http://127.0.0.1:8088/register
```
