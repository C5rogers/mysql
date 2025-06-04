# Installation

```sh
sudo systemctl stop mysql
task compose -- up -d
```

# Checking MYSQL Log

```sh
task log_mysql
```
# Accessing without the ip address
```sh
sudo sh -c 'echo "172.17.0.1 host.docker.internal" >> /etc/hosts'
```

# After that you can access it by the host name of
```sh
host.docker.internal
```

# Connecting with client

```sh
host: localhost
role: root
password: *password less
port: 3306
database: ${MYSQL_DATABASE}
```

# Creating new User with with permissions

```sql
CREATE USER 'user'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'user'@'%';
FLUSH PRIVILEGES;
```

# Creating new Database

```sql
CREATE DATABASE IF NOT EXISTS ${MYSQL_DATABASE};
```

# Creating new Table

```sql
CREATE TABLE IF NOT EXISTS ${MYSQL_DATABASE}.users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
