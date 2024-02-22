# 查看主从复制信息
```redis-cli -p 主/从端口 info replication```

# 查看哨兵信息
```redis-cli -p 哨兵端口 info sentinel```

# master 步骤
```
1.端口
port 6379

2.redis无法设置指定外网ip访问,需要使用防火墙限制
bind 0.0.0.0

3.设定连接主节点所使用的密码
masterauth 123456

4.开启redis密码
requirepass 123456

5.AOF持久化
appendonly yes
```

# slave1 步骤
```
1.端口
port 6380

2.redis无法设置指定外网ip访问,需要使用防火墙限制
bind 0.0.0.0

3.配置master节点信息
replicaof redis-master 6379

4.设定连接主节点所使用的密码
masterauth 123456

5.开启redis密码
requirepass 123456

6.AOF持久化
appendonly yes
```

# slave2 步骤
```
1.端口
port 6381

2.redis无法设置指定外网ip访问,需要使用防火墙限制
bind 0.0.0.0

3.配置master节点信息
replicaof redis-master 6379

4.设定连接主节点所使用的密码
masterauth 123456

5.开启redis密码
requirepass 123456

6.AOF持久化
appendonly yes
```

# sentinel1 步骤
_注意 哨兵配置文件是一个全新的配置文件_
```
1.端口
port 26379

2.监控
sentinel monitor <master-name> <ip> <redis-port> <quorum>  
master-name是为这个被监控的master起的名字
(设置其他名字需要更改所有为mymaster的地方)
ip是被监控的master的IP或主机名。因为Docker容器之间可以使用容器名访问，所以这里写master节点的容器名
redis-port是被监控节点所监听的端口号
quorom设定了当几个哨兵判定这个节点失效后，才认为这个节点真的失效了
sentinel monitor mymaster redis-master 6379 2

3.连接主节点的密码
sentinel auth-pass mymaster 123456
```

# sentinel2 步骤
```
1.端口
port 26380

2.监控
sentinel monitor <master-name> <ip> <redis-port> <quorum>  
master-name是为这个被监控的master起的名字
(设置其他名字需要更改所有为mymaster的地方)
ip是被监控的master的IP或主机名。因为Docker容器之间可以使用容器名访问，所以这里写master节点的容器名
redis-port是被监控节点所监听的端口号
quorom设定了当几个哨兵判定这个节点失效后，才认为这个节点真的失效了
sentinel monitor mymaster redis-master 6379 2

3.连接主节点的密码
sentinel auth-pass mymaster 123456
```

# sentinel3 步骤
```
1.端口
port 26381

2.监控
sentinel monitor <master-name> <ip> <redis-port> <quorum>  
master-name是为这个被监控的master起的名字
(设置其他名字需要更改所有为mymaster的地方)
ip是被监控的master的IP或主机名。因为Docker容器之间可以使用容器名访问，所以这里写master节点的容器名
redis-port是被监控节点所监听的端口号
quorom设定了当几个哨兵判定这个节点失效后，才认为这个节点真的失效了
sentinel monitor mymaster redis-master 6379 2

3.连接主节点的密码
sentinel auth-pass mymaster 123456
```