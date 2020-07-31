# devil


### 一、引用

```bash
source $(dirname $0)/libs/commmon.sh
```

### 二、使用

### 2.1、配置读取

例如，配置文件 `${dirname $0}/conf/devil.ini` 的内容如下：

```
[main]
debug = true
env = develop

[server]
protocol = http
http_port = 9999
enforce_domain = true

[server.ips]
- = 127.0.0.1
- = 127.0.0.2
- = 127.0.0.3

```

读取示例如下:

```bash
#!/bin/bash
# 引入公用函数
source $(dirname $0)/libs/commmon.sh

# 定义配置文件路径
CONF_PATH=$(dirname $0)/conf/devil.ini

# 读取 'server' 配置项下的 'protocol' 的值：
echo "server.protocol is : $(ini_get $CONF_PATH server protocol)"

# 读取 ''server.ips' 下的所有ip地址：
echo "server ips is: $(ini_get $CONF_PATH server.ips -)"
```

输出如下:

```bash
server.protocol is : http
server ips is: 127.0.0.1
127.0.0.2
127.0.0.3
```

### 2.2、表格打印

打印示例如下：

```bash
#!/bin/bash
# 引入公用函数
source $(dirname $0)/libs/commmon.sh

table_column ---- ---    ----
table_column name occupation  birthday
table_column ---- ---    ----
table_column jack teacher 2000-01-05
table_column jack teacher 2000-01-05
table_column jack teacher 2000-01-05
table_column jack teacher 2000-01-05
table_column jack teacher 2000-01-05
table_column jack teacher 2000-01-05
table_print
```

输出如下:

```
|  ----  |  ---         |  ----        |
|  name  |  occupation  |  birthday    |
|  ----  |  ---         |  ----        |
|  jack  |  teacher     |  2000-01-05  |
|  jack  |  teacher     |  2000-01-05  |
|  jack  |  teacher     |  2000-01-05  |
|  jack  |  teacher     |  2000-01-05  |
|  jack  |  teacher     |  2000-01-05  |
|  jack  |  teacher     |  2000-01-05  |
```
