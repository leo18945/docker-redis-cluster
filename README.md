# Docker Compose Redis Cluster

![img](https://itsmetommy.com/wp-content/uploads/docker-redis.jpg)

# Clone git repository

https://github.com/leo18945/docker-redis-cluster

# Build and start all containers

```shell
docker-compose up --build -d
```

# View containers

```shell
docker ps
```

# Logs

To get a better understanding of how the cluster was created, check out the redis-1 and redis-ruby logs.

redis-1 logs

```shell
docker-compose logs redis-1
```

Example

```shell
docker-compose logs redis-1
Attaching to redis-1
redis-1 | 1:C 25 May 00:01:14.227 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
redis-1 | 1:C 25 May 00:01:14.227 # Redis version=4.0.2, bits=64, commit=00000000, modified=0, pid=1, just started
redis-1 | 1:C 25 May 00:01:14.227 # Configuration loaded
redis-1 | 1:M 25 May 00:01:14.227 * No cluster configuration found, I'm 9f0e1bd9ec36a0dd6a72637fecb51c78af4ca8d9
redis-1 | 1:M 25 May 00:01:14.231 * Running mode=cluster, port=7000.
redis-1 | 1:M 25 May 00:01:14.231 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
redis-1 | 1:M 25 May 00:01:14.231 # Server initialized
redis-1 | 1:M 25 May 00:01:14.231 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
redis-1 | 1:M 25 May 00:01:14.231 * Ready to accept connections
redis-1 | 1:M 25 May 00:01:18.978 # configEpoch set to 1 via CLUSTER SET-CONFIG-EPOCH
redis-1 | 1:M 25 May 00:01:18.995 # IP address for this node updated to 10.0.0.2
redis-1 | 1:M 25 May 00:01:23.551 * Slave 10.0.0.6:7004 asks for synchronization
redis-1 | 1:M 25 May 00:01:23.551 * Partial resynchronization not accepted: Replication ID mismatch (Slave asked for '374dc0684d702b4583bf0a393c07309f6bcbe0e0', my replication IDs are '5e945012ec710f579eb4d35aa2c4a996a83812c9' and '0000000000000000000000000000000000000000')
redis-1 | 1:M 25 May 00:01:23.551 * Starting BGSAVE for SYNC with target: disk
redis-1 | 1:M 25 May 00:01:23.551 * Background saving started by pid 13
redis-1 | 13:C 25 May 00:01:23.553 * DB saved on disk
redis-1 | 13:C 25 May 00:01:23.553 * RDB: 0 MB of memory used by copy-on-write
redis-1 | 1:M 25 May 00:01:23.640 * Background saving terminated with success
redis-1 | 1:M 25 May 00:01:23.640 * Synchronization with slave 10.0.0.6:7004 succeeded
redis-1 | 1:M 25 May 00:01:23.944 # Cluster state changed: ok
```

redis-ruby logs

```shell
docker-compose logs redis-ruby
```

Example

```shell
docker-compose logs redis-ruby
Attaching to redis-ruby
redis-ruby | Successfully installed redis-4.0.1
redis-ruby | 1 gem installed
redis-ruby | --2018-05-25 00:01:18-- http://download.redis.io/redis-stable/src/redis-trib.rb
redis-ruby | Resolving download.redis.io (download.redis.io)... 109.74.203.151
redis-ruby | Connecting to download.redis.io (download.redis.io)|109.74.203.151|:80... connected.
redis-ruby | HTTP request sent, awaiting response... 200 OK
redis-ruby | Length: 65991 (64K) [text/plain]
redis-ruby | Saving to: 'redis-trib.rb'
redis-ruby |
redis-ruby | 0K .......... .......... .......... .......... .......... 77% 161K 0s
redis-ruby | 50K .......... .... 100% 3.07M=0.3s
redis-ruby |
redis-ruby | 2018-05-25 00:01:18 (205 KB/s) - 'redis-trib.rb' saved [65991/65991]
redis-ruby |
redis-ruby | >>> Creating cluster
redis-ruby | >>> Performing hash slots allocation on 6 nodes...
redis-ruby | Using 3 masters:
redis-ruby | 10.0.0.2:7000
redis-ruby | 10.0.0.3:7001
redis-ruby | 10.0.0.4:7002
redis-ruby | Adding replica 10.0.0.6:7004 to 10.0.0.2:7000
redis-ruby | Adding replica 10.0.0.7:7005 to 10.0.0.3:7001
redis-ruby | Adding replica 10.0.0.5:7003 to 10.0.0.4:7002
redis-ruby | M: 9f0e1bd9ec36a0dd6a72637fecb51c78af4ca8d9 10.0.0.2:7000
redis-ruby | slots:0-5460 (5461 slots) master
redis-ruby | M: 65af6640288482d4c12758885f2b1fdd2ab45384 10.0.0.3:7001
redis-ruby | slots:5461-10922 (5462 slots) master
redis-ruby | M: 51f892a2dce483b2121c7b5dfb07df5adc7c38ec 10.0.0.4:7002
redis-ruby | slots:10923-16383 (5461 slots) master
redis-ruby | S: 5d274177a8408781e3977329cd839751883a19a9 10.0.0.5:7003
redis-ruby | replicates 51f892a2dce483b2121c7b5dfb07df5adc7c38ec
redis-ruby | S: 43b864b848a5d1731ce6e37a4b3bb315c9584903 10.0.0.6:7004
redis-ruby | replicates 9f0e1bd9ec36a0dd6a72637fecb51c78af4ca8d9
redis-ruby | S: 5d8956bd8960ce14fb4958a61b2ada436c80c9e1 10.0.0.7:7005
redis-ruby | replicates 65af6640288482d4c12758885f2b1fdd2ab45384
redis-ruby | Can I set the above configuration? (type 'yes' to accept): >>> Nodes configuration updated
redis-ruby | >>> Assign a different config epoch to each node
redis-ruby | >>> Sending CLUSTER MEET messages to join the cluster
redis-ruby | Waiting for the cluster to join...
redis-ruby | >>> Performing Cluster Check (using node 10.0.0.2:7000)
redis-ruby | M: 9f0e1bd9ec36a0dd6a72637fecb51c78af4ca8d9 10.0.0.2:7000
redis-ruby | slots:0-5460 (5461 slots) master
redis-ruby | 1 additional replica(s)
redis-ruby | S: 43b864b848a5d1731ce6e37a4b3bb315c9584903 10.0.0.6:7004
redis-ruby | slots: (0 slots) slave
redis-ruby | replicates 9f0e1bd9ec36a0dd6a72637fecb51c78af4ca8d9
redis-ruby | M: 51f892a2dce483b2121c7b5dfb07df5adc7c38ec 10.0.0.4:7002
redis-ruby | slots:10923-16383 (5461 slots) master
redis-ruby | 1 additional replica(s)
redis-ruby | M: 65af6640288482d4c12758885f2b1fdd2ab45384 10.0.0.3:7001
redis-ruby | slots:5461-10922 (5462 slots) master
redis-ruby | 1 additional replica(s)
redis-ruby | S: 5d8956bd8960ce14fb4958a61b2ada436c80c9e1 10.0.0.7:7005
redis-ruby | slots: (0 slots) slave
redis-ruby | replicates 65af6640288482d4c12758885f2b1fdd2ab45384
redis-ruby | S: 5d274177a8408781e3977329cd839751883a19a9 10.0.0.5:7003
redis-ruby | slots: (0 slots) slave
redis-ruby | replicates 51f892a2dce483b2121c7b5dfb07df5adc7c38ec
redis-ruby | [OK] All nodes agree about slots configuration.
redis-ruby | >>> Check for open slots...
redis-ruby | >>> Check slots coverage...
redis-ruby | [OK] All 16384 slots covered.
```

# Connect to one of the masters

**Note**: -c Enable cluster mode (follow -ASK and -MOVED redirections)

```shell
docker exec -it redis-1 redis-cli -c -p 7000
```

# Create keys

```shell
127.0.0.1:7000> set mykey1 1
OK
127.0.0.1:7000> set mykey3 3
-> Redirected to slot [9990] located at 10.0.0.3:7001
OK
10.0.0.3:7001> set mykey2 2
-> Redirected to slot [14119] located at 10.0.0.4:7002
OK
10.0.0.4:7002> get mykey1
-> Redirected to slot [1860] located at 10.0.0.2:7000
"1"
10.0.0.2:7000> get mykey3
-> Redirected to slot [9990] located at 10.0.0.3:7001
"3"
10.0.0.3:7001> get mykey2
-> Redirected to slot [14119] located at 10.0.0.4:7002
"2"
10.0.0.4:7002>
```

**Error warning**

If you do not use the -c option to connect to the cluster, you will run into the following errors.

```shell
docker exec -it redis-1 redis-cli -p 7000
127.0.0.1:7000> set mykey1 1
OK
127.0.0.1:7000> set mykey2 2
(error) MOVED 14119 10.0.0.4:7002
127.0.0.1:7000> set mykey3 3
(error) MOVED 9990 10.0.0.3:7001
127.0.0.1:7000> get mykey1
"1"
127.0.0.1:7000> get mykey2
(error) MOVED 14119 10.0.0.4:7002
```

# View nodes

```shell
127.0.0.1:7000> cluster nodes
```

Example

```shell
127.0.0.1:7000> cluster nodes
43b864b848a5d1731ce6e37a4b3bb315c9584903 10.0.0.6:7004@17004 slave 9f0e1bd9ec36a0dd6a72637fecb51c78af4ca8d9 0 1527206692231 5 connected
9f0e1bd9ec36a0dd6a72637fecb51c78af4ca8d9 10.0.0.2:7000@17000 myself,master - 0 1527206690000 1 connected 0-5460
51f892a2dce483b2121c7b5dfb07df5adc7c38ec 10.0.0.4:7002@17002 master - 0 1527206691624 3 connected 10923-16383
65af6640288482d4c12758885f2b1fdd2ab45384 10.0.0.3:7001@17001 master - 0 1527206692000 2 connected 5461-10922
5d8956bd8960ce14fb4958a61b2ada436c80c9e1 10.0.0.7:7005@17005 slave 65af6640288482d4c12758885f2b1fdd2ab45384 0 1527206690198 6 connected
5d274177a8408781e3977329cd839751883a19a9 10.0.0.5:7003@17003 slave 51f892a2dce483b2121c7b5dfb07df5adc7c38ec 0 1527206691217 4 connected
```

# View slots

```shell
127.0.0.1:7000> cluster slots
```

Example

```shell
127.0.0.1:7000> cluster slots
1) 1) (integer) 0
   2) (integer) 5460
   3) 1) "10.0.0.2"
      2) (integer) 7000
      3) "9f0e1bd9ec36a0dd6a72637fecb51c78af4ca8d9"
   4) 1) "10.0.0.6"
      2) (integer) 7004
      3) "43b864b848a5d1731ce6e37a4b3bb315c9584903"
2) 1) (integer) 10923
   2) (integer) 16383
   3) 1) "10.0.0.4"
      2) (integer) 7002
      3) "51f892a2dce483b2121c7b5dfb07df5adc7c38ec"
   4) 1) "10.0.0.5"
      2) (integer) 7003
      3) "5d274177a8408781e3977329cd839751883a19a9"
3) 1) (integer) 5461
   2) (integer) 10922
   3) 1) "10.0.0.3"
      2) (integer) 7001
      3) "65af6640288482d4c12758885f2b1fdd2ab45384"
   4) 1) "10.0.0.7"
      2) (integer) 7005
      3) "5d8956bd8960ce14fb4958a61b2ada436c80c9e1"
```

# Clean up

```shell
docker-compose down
```

