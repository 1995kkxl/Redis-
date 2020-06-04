"# Redis-" 
redis一键安装脚本  默认配置文件/conf
需要部署集群  升级ruby2.4版本+

新建集群配置文件
配置机器1

    在演示中，172.16.179.130为当前ubuntu机器的ip
    在172.16.179.130上进⼊Desktop⽬录，创建conf⽬录

    在conf⽬录下创建⽂件7000.conf，编辑内容如下

    port 7000
    bind 172.16.179.130
    daemonize yes
    pidfile 7000.pid
    cluster-enabled yes
    cluster-config-file 7000_node.conf
    cluster-node-timeout 15000
    appendonly yes

    在conf⽬录下创建⽂件7001.conf，编辑内容如下

    port 7001
    bind 172.16.179.130
    daemonize yes
    pidfile 7001.pid
    cluster-enabled yes
    cluster-config-file 7001_node.conf
    cluster-node-timeout 15000
    appendonly yes

    在conf⽬录下创建⽂件7002.conf，编辑内容如下

    port 7002
    bind 172.16.179.130
    daemonize yes
    pidfile 7002.pid
    cluster-enabled yes
    cluster-config-file 7002_node.conf
    cluster-node-timeout 15000
    appendonly yes

    总结：三个⽂件的配置区别在port、pidfile、cluster-config-file三项

    使⽤配置⽂件启动redis服务

    redis-server 7000.conf
    redis-server 7001.conf
    redis-server 7002.conf
    
    
    
 机器2
 配置机器2

    在演示中，172.16.179.131为当前ubuntu机器的ip
    在172.16.179.131上进⼊Desktop⽬录，创建conf⽬录

    在conf⽬录下创建⽂件7003.conf，编辑内容如下

    port 7003
    bind 172.16.179.131
    daemonize yes
    pidfile 7003.pid
    cluster-enabled yes
    cluster-config-file 7003_node.conf
    cluster-node-timeout 15000
    appendonly yes

    在conf⽬录下创建⽂件7004.conf，编辑内容如下

    port 7004
    bind 172.16.179.131
    daemonize yes
    pidfile 7004.pid
    cluster-enabled yes
    cluster-config-file 7004_node.conf
    cluster-node-timeout 15000
    appendonly yes

    在conf⽬录下创建⽂件7005.conf，编辑内容如下

    port 7005
    bind 172.16.179.131
    daemonize yes
    pidfile 7005.pid
    cluster-enabled yes
    cluster-config-file 7005_node.conf
    cluster-node-timeout 15000
    appendonly yes

    总结：三个⽂件的配置区别在port、pidfile、cluster-config-file三项

    使⽤配置⽂件启动redis服务

    redis-server 7003.conf
    redis-server 7004.conf
    redis-server 7005.conf


部署脚本（拷贝redis-trib.rb/bin目录下） 需升级ruby！！

redis-trib.rb create --replicas 1 172.16.179.130:7000 172.16.179.130:7001 172.16.179.130:7002 172.16.179.131:7003 172.16.179.131:7004 172.16.179.131:7005
