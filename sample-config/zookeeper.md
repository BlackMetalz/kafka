1. For Single Mode
```
# the directory where the snapshot is stored.
dataDir=/data/zk_data
# the port at which the clients will connect
clientPort=2181
# disable the per-ip limit on the number of connections since this is a non-production config
maxClientCnxns=0
# Disable the adminserver by default to avoid port conflicts.
# Set the port to something non-conflicting if choosing to enable this
admin.enableServer=false
# admin.serverPort=8080
```

2. For cluster mode
```
# http://hadoop.apache.org/zookeeper/docs/current/zookeeperAdmin.html
# The number of milliseconds of each tick
tickTime=2000
# The number of ticks that the initial
# synchronization phase can take
initLimit=3000
# The number of ticks that can pass between
# sending a request and getting an acknowledgement
syncLimit=10
# the directory where the snapshot is stored.
dataDir=/data/zookeeper-data/zookeeper-3.5.8-2181/data
# Place the dataLogDir to a separate physical disc for better performance
# dataLogDir=/disk2/zookeeper

# the port at which the clients will connect
clientPort=2181

# specify all zookeeper servers
# The fist port is used by followers to connect to the leader
# The second one is used for leader election

server.1=10.3.48.54:2888:3888
server.2=10.3.48.56:2888:3888
server.3=10.3.48.82:2888:3888

# Limits the number of concurrent connections (at the socket level) that a single client, identified by IP address, may make to a single member of the ZooKeeper ensemble. This is used to prevent certain classes of DoS attacks, including file descriptor exhaustion. The default is 60. Setting this to 0 entirely removes the limit on concurrent connections.
maxClientCnxns= 0

# The maximum session timeout in milliseconds that the server will allow the client to negotiate. Defaults to 20 times the tickTime.
maxSessionTimeout=60000000

# When enabled, ZooKeeper auto purge feature retains the autopurge.snapRetainCount most recent snapshots and the corresponding transaction logs in the dataDir and dataLogDir respectively and deletes the rest. Defaults to 3. Minimum value is 3.
autopurge.snapRetainCount=10

# The time interval in hours for which the purge task has to be triggered. Set to a positive integer (1 and above) to enable the auto purging. Defaults to 0.
autopurge.purgeInterval=1

# To avoid seeks ZooKeeper allocates space in the transaction log file in
# blocks of preAllocSize kilobytes. The default block size is 64M. One reason
# for changing the size of the blocks is to reduce the block size if snapshots
# are taken more often. (Also, see snapCount).
preAllocSize=131072

# Clients can submit requests faster than ZooKeeper can process them,
# especially if there are a lot of clients. To prevent ZooKeeper from running
# out of memory due to queued requests, ZooKeeper will throttle clients so that
# there is no more than globalOutstandingLimit outstanding requests in the
# system. The default limit is 1,000.ZooKeeper logs transactions to a
# transaction log. After snapCount transactions are written to a log file a
# snapshot is started and a new transaction log file is started. The default
# snapCount is 10,000.
snapCount=3000000

# If this option is defined, requests will be will logged to a trace file named
# traceFile.year.month.day.
#traceFile=

# Leader accepts client connections. Default value is "yes". The leader machine
# coordinates updates. For higher update throughput at thes slight expense of
# read throughput the leader can be configured to not accept clients and focus
# on coordination.
leaderServes=yes

# When set to false, a single server can be started in replicated mode, a lone participant can run with observers, and a cluster can reconfigure down to one node, and up from one node. The default is true for backwards compatibility. It can be set using QuorumPeerConfig's setStandaloneEnabled method or by adding "standaloneEnabled=false" or "standaloneEnabled=true" to a server's config file.
standaloneEnabled=false

requireClientAuthScheme=sasl
authProvider.1=org.apache.zookeeper.server.auth.SASLAuthenticationProvider
#authProvider.2=org.apache.zookeeper.server.auth.SASLAuthenticationProvider
#authProvider.3=org.apache.zookeeper.server.auth.SASLAuthenticationProvider
jaasLoginRenew=3600000

4lw.commands.whitelist=mntr,conf,ruok
```
